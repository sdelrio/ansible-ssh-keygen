ssh-keygen
==========

A role to create a ssh key pairs on your `$HOME/.ssh`

Requirements
------------

Nothing special, the role is designed to work as a local deployment for my computers, so I don't remember to create the keys in the last moment when I need to copy my key to use on a ssh conection or github.

For now only tested on Debian 8, that's why there is as task for it. Should work on CenOS/Redhat without many changes.

Role Variables
--------------

- `ssh_keygen_bits`: with defaunt value to `4096` bits.
- `ssh_keygen_email`:  With a default value of "{{ ansible_ssh_user }}@users.noreply.github.com", because was in mind to use as github primary use.
- `ssh_keygen_user`: `{{ ansible_ssh_user }}` the user you connect, on local run should be your user.
- `ssh_keygen_types`: By default generate two types
  - rsa
  - ed25519 

Dependencies
------------

No dependencies on other roles.

Example Playbook
----------------

How to use the role on local (make sure your user has sudo privilege):


```
---
- name: Local computer
  hosts: localhost
  sudo: True
  pre_tasks:
    - name: update APT cache
      apt: update_cache=yes cache_valid_time=28800
      when: ansible_os_family == 'Debian'

  roles:
    - role: ssh-keygen
      ssh_keygen_email: myemail@mydomain.com
```


License
-------

BSD

