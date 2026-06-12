---
title: "root account cant login"
date: 2020-12-27
forum: New to Ubuntu
---

### Post by shootify on 2020-12-27
i just installed ubuntu server 20.04, during installation it prompted to create  a user and password which i did, however no i need to run an application that needs to be run as a root, i did enable ssh root access however which password should i use since its not getting the one of the user i created during the installation, please clarify this to me. thanks in advanced.

---

### Post by ActionParsnip on 2020-12-27
Just log in as the user you made and prefix your command with "sudo" and it'll run as root.

---

### Post by TheFu on 2020-12-27
Ubuntu generally doesn't allow direct access to the root account.  Logging in as root is prohibited.  Remote access by root is prohibited.  
We use **sudo** to temporarily elevate privileges for a command/script, when needed, then drop back to a normal privilege level. Only certain userids are allowed that, by being members of the sudo group.

Please put the remote root access setting back. It is a liability to be avoided.

In general, enabling the root account and remote root access are things that if you have to ask how, then it shouldn't be done.  There are a few times where remote root is needed, but only for specific, locked down, purposes. I allow my backup server, and nowhere else, remote root access, for example. It can only run 2 commands and only with very specific options.

There is a sudoroot guide on help.ubuntu.com with more details, should you need it. Forum polices basically say to direct you there, I believe.

---

### Post by shootify on 2020-12-27
undestrood. thanks

---

### Post by mastablasta on 2020-12-29
Wow, this documentation stuff is now so difficult to find.

ssh: [https://ubuntu.com/server/docs/service-openssh](https://ubuntu.com/server/docs/service-openssh)

root sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

in terminal: 
man sudo

don't use root, it is not needed. use sudo instead.

---

