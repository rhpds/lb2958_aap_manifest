# Summit Lightspeed Chatbot Lab

Lab environment automation for bootstrapping AAP 2.5 deployed in Openshift with the Lightspeed Chatbot.

This Ansible role uploads an AAP 2.6 manifest to an existing AAP installation and can optionally deploy Lightspeed as a Day 2 operation.

## Requirements

- An existing AAP installation on OpenShift
- Access to the AAP manifest file
- Proper OpenShift credentials with access to the AAP namespace

## Usage

### Set Env Vars for Lightspeed

If you want to deploy Lightspeed with WCA integration, you can set the following environment variables before running the playbook:

```bash
export LIGHTSPEED_WCA_ENABLED=false
export LIGHTSPEED_CHATBOT_TOKEN="your-chatbot-token"
```

### Create vars.yml from template and run playbook

The easiest way to run this role is by using a vars.yml file:

1. Copy the example vars file:
   ```bash
   cp vars.yml.example vars.yml
   ```

2. Edit the vars.yml file with your specific values:
   ```bash
   vi vars.yml
   ```

Required variables to change:
- lb2958_aap_manifest_url or lb2958_aap_manifest_local_path
- lb2958_aap_manifest_aap_hostname
- lb2958_aap_manifest_aap_password
- aap_namespace
- aap_name
- lightspeed_chatbot_url

3. Run the playbook directly using ansible-playbook:
   ```bash
   ansible-playbook bootstrap-lightspeed-chatbot.yml -e @vars.yml
   ```

This approach allows you to keep your configuration separate from the code and easily update variables without modifying the playbook.

> Note: It will take about 10 minutes for Lightspeed to deploy and registry with AAP.
