---
title: "Creating a user through Ansible with a password"
date: 2019-12-15
forum: Programming Talk
---

### Post by john960 on 2019-12-15
Hi all

Ansible does not seem to take plain text for password. Instead of having to copy paste an encrypted password, is there any other way to get Ansible to do it on its own?

Thanks

---

### Post by TheFu on 2019-12-15
> **john960 said:**
> Hi all

Ansible does not seem to take plain text for password. Instead of having to copy paste an encrypted password, is there any other way to get Ansible to do it on its own?

Thanks

Seems like a very specific devops question.  We don't use passwords. We install ssh-keys into new VMs.

---

### Post by arytmw on 2019-12-15
Normally you need to input the password with SHA-512 encryption when creating a user via Ansible. 

You can use the following playbook to have Ansible do it for you, 
```
[COLOR=#666666][FONT=&amp]---[/FONT][/COLOR]- name: user creation
  hosts: all
  tasks:
    - name: creating a user with a defined password
      user:
                name: enterusername
                password: "{{ mypassword | password_hash('sha512') }}" [COLOR=#666666][FONT=&amp]                
                state: present
[/FONT][/COLOR]
```
Original source: [https://networknuts.net/basic-ansible-playbooks/](https://networknuts.net/basic-ansible-playbooks/)

---

