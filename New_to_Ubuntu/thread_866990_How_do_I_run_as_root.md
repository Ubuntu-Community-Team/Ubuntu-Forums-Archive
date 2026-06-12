---
title: "How do I run as root?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by mczonie on 2008-07-22
Hi, all. 

How do I run as root? More importantly, how do I *not* run as root? I understand that not running as root is the most important aspect of insuring your computers security. 

Also, is running as root the same as running as administrator? 

Sorry about the stupid questions, but I know very little about computers and even less about Linux.

TIA.

---

### Post by tech0007 on 2008-07-22
You only need to run as root when you install programs, update ubuntu or change system wide settings. You should use either gksu or gksudo (press alt-f2).

Use your regular account for all other stuff (browsing, email, printing,e tc). 

Running as root is the same as running as admin in windoze world.

---

### Post by Potatoj316 on 2008-07-22
You are not root by default.  Everything you do is done by the normal user.  If it ever asks for your password while trying to run a program then you are root in that program.  If you are using the terminal then you are also not root.  To become root temporarialy (one command only) then put a sudo infront of that command.

---

### Post by Vishal Agarwal on 2008-07-22
Use command > sudo -i
This will give you the root power.

---

### Post by Lord DarkPat on 2008-07-22
Root is rather different from Admin, but te concepts are basically the same.
to run a command as root(this is probably the most common case)
run this in the command line
```
sudo *command*
eg:- sudo apt-get update
```
if you want to go into root mode, then type commands,
```
sudo su
apt-get update
```
:KS have fun

---

### Post by Titan8990 on 2008-07-22
Root is locked by default and you will not be able to gain root access like others have said without unlocking it. It is my understanding that there is a policy on the forums that we do not tell people how to unlock root.

---

