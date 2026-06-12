---
title: "what does this mean and how do I get superuser permission?"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-07-26
allan@allan-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
allan@allan-laptop:~$

---

### Post by oldos2er on 2008-07-26
sudo dpkg --configure -a

---

### Post by El Conquistador on 2008-07-26
ok well all the times ive ever had to run that its because there is something wrong with the acket manager so all that does for me is automatically fix it. i wuld think its usually a badly installed package. but to get superuser just type in "sudo" before every command that requires superuser privilages.

---

### Post by eightmillion on 2008-07-26
saskatchewan, your regular user account doesn't have permissions to do actions that could change your system. This is done for security. To run that command as the superuser you need to do this...
> sudo dpkg --configure -a
Sudo lets you run commands as a privileged user. It literally means **s**uper **u**ser **do**. It will ask you for your password. This is the password that you use to log on to ubuntu with. Be careful when running any command as the root user.

---

### Post by palani.ultimateguy on 2008-11-01
I dont get the super user permission.It says that password error.
I have a user name as palani and set a password for it while installing it but when i type that password when it ask for super user password it throws an access denied message.

help me to get super user permission

---

### Post by bikerharis on 2009-01-12
^^^^^^ i am facing the same problem. While give my password it says
 su: Authentication failure

somebody please help.

---

### Post by donkyhotay on 2009-01-12
incorrect post

---

### Post by PirateChef on 2009-01-12
I'll ask the obvious: Is the CAPS LOCK off?

---

### Post by oldos2er on 2009-01-12
> **bikerharis said:**
> ^^^^^^ i am facing the same problem. While give my password it says
 su: Authentication failure

somebody please help.

 Don't use 'su', use 'sudo'

---

### Post by mjheagle8 on 2009-01-12
if you put in your password and it says that it is incorrect, there are two possible problems.
1) you typed the password
2) you are not the root user. if there is someone else who is on your computer, they might be the root user.

---

### Post by bodhi.zazen on 2009-01-12
> **bikerharis said:**
> ^^^^^^ i am facing the same problem. While give my password it says
 su: Authentication failure

somebody please help.

> **mjheagle8 said:**
> if you put in your password and it says that it is incorrect, there are two possible problems.
1) you typed the password
2) you are not the root user. if there is someone else who is on your computer, they might be the root user.

As has been pointed out in this thread several times, Ubuntu uses sudo.

The root account is locked.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by flyingsliverfin on 2009-01-12
I think you can also become root by typing

sudo su

it requires your password, not the root's
(incase you don't know it)

---

### Post by mjheagle8 on 2009-01-12
> **flyingsliverfin said:**
> I think you can also become root by typing

sudo su

it requires your password, not the root's
(incase you don't know it)

i dont think this is true, to become the root user or super user, you have to have that password. this would defeat the purpose of having a root or super user.

---

### Post by flyingsliverfin on 2009-01-12
I agree

I cant try it now though because I am in a computer club in school and they have xp

---

### Post by moonoo on 2009-01-12
[FONT="Courier New"]sudo su[/FONT]

with 'your' password puts you in root

---

### Post by bodhi.zazen on 2009-01-12
> **mjheagle8 said:**
> i dont think this is true, to become the root user or super user, you have to have that password. this would defeat the purpose of having a root or super user.

> **flyingsliverfin said:**
> I agree

I cant try it now though because I am in a computer club in school and they have xp

sudo su == "run su as root"

su, with no arguments defaults to root. Root can become root (or any other system users who may log in) without a password.

> bodhi@jaunty:~$ **[color=red]sudo su**[/color]
[color=blue][sudo] password for **bodhi**:[/color]
**[color=darkred]root@jaunty:/home/bodhi#**[/color]

---

### Post by mjheagle8 on 2009-01-12
> **bodhi.zazen said:**
> sudo su == "run su as root"

su, with no arguments defaults to root. Root can become root (or any other system users who may log in) without a password.

thank you for the clarification bodhi,

---

### Post by bodhi.zazen on 2009-01-12
> **mjheagle8 said:**
> thank you for the clarification bodhi,

You are most welcome.

---

