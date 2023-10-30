# ansible-network-virt

This repo contains Ansible code which deploys RHEL + QEMU/KVM on AWS EC2 Metal instances for purposes of running virtualized network devices. In specific, this was made to run a zero-touch provisioning workshop in the cloud where students can have full control over DHCP. However this could also be used for purposes beyond that.

## How to deploy ZTP workshop
1. Get image files matching the `qemu_images` value within the `qemu` role (or adjust the value to what you have). Place in `files/`.
2. Determine number of students. Optional, defaults to 1. Pass in as `num_students`.
3. Get Red Hat Management API offline token from https://access.redhat.com/management/api. Pass in as `aap_offline_token`.
4. Get a subscription manifest for Controller, name it `manifest.zip`. Place in `files/`.
5. Ensure you have AWS credentials available via the `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` environment variables.

That's it - run `playbook_deploy.yml` with the above extra_vars. Everything runs in one EC2 instance and can be mostly torn down by terminating it.
