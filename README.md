CentOS 7 setup
=========

Execute the following processing.

* Disable SELinux
* Add user
* Disable root login
* Disable password login
* Change ssh port
* Setup firewall(ssh and http)

You must create a RSA key in advance.

Requirements
------------

This role requires Ansible 1.9 or higher.

Role Variables
--------------

```
main_user_name: momo
# default password is "sora". created by # python -c "from passlib.hash import sha512_crypt; import getpass; print sha512_crypt.encrypt(getpass.getpass())"
main_user_password: $6$rounds=656000$kXdiHg0O8QL0FcEa$rbTKjamQQduBhT2NG2yoXt7OJCeHTuthq/.i.ALT4ViVhpldcLcWDQWe41sTdBor294gIhv5Nsl3fCJIC33V50 
ssh_port: 10022
auth_key_path: id_rsa.pub

```

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      user: root
      vars_prompt:
        - name: main_user_password
          prompt: "Input newuser passowrd"
          encrypt: sha512_crypt
          confirm: yes
      roles:
         - { role: tsyki.centos7-setup, auth_key_path: ~/.ssh/id_rsa.pub , main_user_name: piyo, ssh_port: 20022 }

License
-------

BSD

Author Information
------------------

Toshiyuki Imaizumi
