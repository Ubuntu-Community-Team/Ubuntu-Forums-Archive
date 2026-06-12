---
title: "Can't login"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by JPrice604 on 2008-09-08
Hi,
I'm using the AMD 64 "Hardy Heron" version, and the installation/partitioning went smoothly but when I try to log in I get sent back to the login screen with a message saying that my last session was less than ten seconds long.  I've tried booting up in safe mode but most things I've attemped in safe mode freeze the computer.  I've double and triple checked all my hardware configuration and it all seems to be right.  Any suggestions?:(

---

### Post by 44tr on 2008-09-08
> **JPrice604 said:**
> Hi,
I'm using the AMD 64 "Hardy Heron" version, and the installation/partitioning went smoothly but when I try to log in I get sent back to the login screen with a message saying that my last session was less than ten seconds long.  I've tried booting up in safe mode but most things I've attemped in safe mode freeze the computer.  I've double and triple checked all my hardware configuration and it all seems to be right.  Any suggestions?:(

Does it login and then log you back out?  Exactly what do you see when you try to login?

---

### Post by ninch on 2008-09-08
I think we need a bit more information on what exactly you see, as the person posted above...if you want you can try using the cd and select the option "try ubuntu without changing computer." This can tell you if its a download error or a computer error.

I read this on a different site, though:

try logging in in terminal and then run the follow command. 
Then reboot:

sudo dpkg-reconfigure ubuntu-desktop

not sure what it does exactly, though. I am relatively new.

Hope this helps.

---

### Post by alienexplorers on 2008-09-08
Does it mention anything about not being able to find your home folder?

---

### Post by JPrice604 on 2008-09-08
It starts to log in for a brief second then gives a quick flash of a black screen then back to the log in screen with the message "Your last session was less than ten seconds long, if you did not log out there may be insufficient memory. Try safemode to fix the problem."
However, I have 150GB free on that partition so I can't see it being a memory problem.

---

### Post by ninch on 2008-09-08
if you just downloaded a huge update, the space on your disk may not be sufficient.

log in the terminal and type in

df -h

It will tell you if the disk is full or how much space is left.
To make a little space you can type:

sudo apt-get clean

and it will delete all packages which were downloaded with your last updates.

EDIT

nevermind :(

---

### Post by alienexplorers on 2008-09-08
How much ram do you have on your system and what size swap file do you have?  Try booting into recovery mode and login.  At the prompt enter:
> chown yourname:yourgroup /home/name of your home directory
Then reboot and see what happens.

---

### Post by JPrice604 on 2008-09-09
I have 2GB RAM. Thanks I'll give that a try. :)

---

