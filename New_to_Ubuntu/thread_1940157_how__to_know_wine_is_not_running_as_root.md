---
title: "how  to know wine is not running as root?"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by mustafi05 on 2012-03-13
in my 64 bit ubuntu 11.10 i installed wine as a standard user from ubuntu software centre . before installing it asked for super user's password . i give it. now it is installed . but i can not understnd wheather it is running as root or not. so, how to know whether i am running wine as root or not? if i am running wine as root, how to fix it?

---

### Post by Nytram on 2012-03-13
The root user requiring a password is always used to install software. Wine won't be running as root unless you start it with **sudo wine** (it will be running as a regular user.)

---

### Post by mustafi05 on 2012-03-13
so i must sure that i am not running wine as root?

---

### Post by Nytram on 2012-03-13
It will only be running as root if you start **wine** with the prefix **gksu** or **sudo** in a terminal.

If you type this command into a terminal it will show which programs are running as root and which as regular user:

> ps u -A

---

### Post by The Cog on 2012-03-13
When you launch a program, it then runs under your account, and that includes wine. So if you just launch "wine whatever.exe" then that will run under your account, with your rights and privileges.

There are perhaps half-a-dozen programs that will run as root when you start them, but you don't need to worry about them - they are special admin programs.

In case you didn't realise, prefixing a launch command with sudo will launch a program to run as root instead of as yourself. This is needed mainly when you are performing admin tasks. 

Incidentally, sudo is one of the few programs that runs as root when you launch it, and it does this so it can launch other things that you ask it to as root.

P.S.
After launching wine, you can use the command
```
ps -ef | grep wine
```
to see the wine process and the user id it's running with.

---

### Post by grahammechanical on 2012-03-13
This will help you to understand the differences between Ubuntu and other Linux distributions regarding running as root.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

You will see that Ubuntu is protecting us from what you are worried about.

You only authorised the installation of wine. You did not give it root or administrator privileges.

Regards.

---

### Post by mustafi05 on 2012-05-22
thanks all of your suggestion were helpful.

---

