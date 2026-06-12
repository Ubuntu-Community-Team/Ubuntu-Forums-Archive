---
title: "[SOLVED] can not log in as &amp;quot;su&amp;quot;"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-09
hey, I just got my dell inspiron mini 9 pre-installed with Ubuntu 8.04 LTS this friday. I was at this bookstore and I've picked up this UK magazine about learning linux.

anyways I was trying out the bash command lines.

I typed in "su" which the magazine states that it stands for Super User. and than I typed in my password. it failed. It failed multi times.

Did I not make a root user login? or was it something else.

lucky, at the bookstore. Someone over heard about linux. and he says he teaches at a local community college class for fedora/redhat linux.

he told me that Ubuntu doesn't let me log in as "su" because it is a security thing. and it makes ubuntu safer.

I think might be the answer for why it doesn't work.

am i mistaken something? anyone can elaborate this?

---

### Post by roger_1960 on 2008-11-09
Hi

You need to type sudo before the command It asks for your password which wont appear.  By default this gives you 'root' ie superuser permissions for a few minutes (after which you will need to do it again.  Be careful!!  Suggest you read this 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by PointyWombat on 2008-11-09
Hi,

The 'su' command lets you switch user (change to another account), and if you don't supply a user name, it switches you to the root account, providing you enter the root password. There is a root account in Ubuntu, however unlike a lot of other unix/linux distros, the account is locked and not intended to be used directly.  To gain the priviledge of the root account, you should use the 'sudo' command.

Ubuntu does do things differently than some other distro, and it would be worth your while to focus on material which is Ubuntu centric, rather than Fedora or RedHat for example, simply to avoid confusion.

---

### Post by Cannaregio on 2008-11-09
You can get longtime root through 
```
sudo -i
```
but that's insane and you gonna pay for that soon or later, as we all did.

So use [COLOR="Blue"]sudo[/COLOR] for each command (or [COLOR="#0000ff"]gksudo[/COLOR] if you launch a graphical application like gedit), and type your password each time, and be happy.

---

