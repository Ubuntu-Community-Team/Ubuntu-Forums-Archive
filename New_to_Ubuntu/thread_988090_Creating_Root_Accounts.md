---
title: "Creating Root Accounts"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Drezard on 2008-11-20
I have a VPS with Ubuntu Server 8.04 installed on it. It has the root account enabled. First things first. I want to set up a new user account that is going to be the 'root' account and then I want to disable the root account. Any ideas how I would do this?

Daniel

---

### Post by rampageoberon on 2008-11-20
In ubuntu the root account is disabled by default. When you initially create a new account during install it will add you to the sudoers file.

you might want to look at editing the sudoers file with the users you need

hope that helps

edit: you can disable the account using 'usermod' so ```
usermod -L root
``` but i would personally not do this, instead might be worth modifyng the password key in /etc/shadow

---

