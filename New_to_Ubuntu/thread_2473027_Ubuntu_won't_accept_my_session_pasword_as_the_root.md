---
title: "Ubuntu won't accept my session pasword as the root password"
date: 2022-03-21
forum: New to Ubuntu
---

### Post by vramirez2 on 2022-03-21
Hi all, I hope you all are having a good day.


I'm trying to install flatpack to install bottles in ubuntu 18.04 LTS but when I try to do it by console and I write the session password as the root password then ubuntu doesn't accept it and I don't remember that ubuntu asked my about a root or administrator password when I installed it, in fact, when I install any program from the store then the password it ask is the session password.

---

### Post by deadflowr on 2022-03-21
What is the command you are trying?
And what does the command
```
id
```
output?

> I don't remember that ubuntu asked my about a root or administrator password when I installed it,

Ubuntu doesn't ask you to set a root password, all admin level stuff is done through the sudo and policykit programs by an admin level user.
The first created user is typically set with full admin rights.
(Subsequent users typically do not have admin rights and would have to have those manually added to them)

A little about sudo: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo") 
Even less about policykit: [http://manpages.ubuntu.com/manpages/bionic/en/man8/polkit.8.html#overview]("http://manpages.ubuntu.com/manpages/bionic/en/man8/polkit.8.html#overview")

---

### Post by ActionParsnip on 2022-03-21
There is no root password in Ubuntu (by default). Just prefix commands with "sudo" and they will run as root. You will be asked to authenticate and you will type your own password (You will see no feedback as you type).

---

### Post by oldos2er on 2022-03-22
Please answer deadflowr's question about the actual command you ran. ```
flatpak install bottles
``` shouldn't require a password.

---

### Post by TheFu on 2022-03-22
> **ActionParsnip said:**
> There is no root password in Ubuntu (by default). Just prefix commands with "sudo" and they will run as root. You will be asked to authenticate and you will type your own password (You will see no feedback as you type).

Only for userids in the 'sudo' group. 
userids not in the sudo group, as shown by the '**id**' command, cannot use sudo.

---

