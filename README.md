# ansible-adauth

Ansible role to join a Linux Machine (Tested on Fedora and Ubuntu) to an Acive Directory domain using `realm`. The role will also allow specified groups to login and add them to sudoers.

# Variables
```yaml
# Vars general
domain_full: teamn.isucdc.com # The domain you wish to join
adauth_username: username # A user with permission to join the domain
adauth_password: password
# Groups who are allowed to login to the machine
ad_groups:
  - name: Domain Admins
  - name: Other Group
    sudo_access: true
  - name: Enterprise Admins
    sudo_access: true
    sudoers_template: '%Enterprise\ Admins ALL=(ALL) NOPASSWD:ALL'
```

# Running
```

- hosts: linux_boxes
  roles:
   - role: ansible-adauth
     domain_name: teamn.isucdc.com
     adauth_username: username
     adauth_password: password
     ad_groups:
       - name: Domain Admins
       - name: Other Group
         sudo_access: true
       - name: Enterprise Admins
         sudo_access: true
         sudoers_template: '%Enterprise\ Admins ALL=(ALL) NOPASSWD:ALL'

```
