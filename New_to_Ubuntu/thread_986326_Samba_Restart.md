---
title: "Samba Restart"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Thelasko on 2008-11-18
I have Samba configured to allow access to everyone without requiring a password.  However, every day or so, I have to restart Samba or else clients trying to access my shares are given a password dialogue box.

The issue only applies to shared files, my shared printer always works fine.

---

### Post by Titan8990 on 2008-11-18
I don't have a solution to your problem but I can suggest a temporary workaround. 

Set up a cron job to restart samba once per day.

---

### Post by Thelasko on 2008-11-18
> **Titan8990 said:**
> I don't have a solution to your problem but I can suggest a temporary workaround. 

Set up a cron job to restart samba once per day.

I've actually thought about that.  I'm just wondering if there's something I'm doing wrong in the first place.

---

### Post by Kellemora on 2008-11-19
Hi TL

We have bigger problems than that, but what I've done is simply removed the share password, made it blank, so if the box does pop up, they just hit enter!  I did something else also that was recommended here, but sorry, I remember for the life of me what it was.

Our network goes down everytime we get an update and the only way to get it back again is to do that 3 reboot routine I've mentioned here several times.  Restarting Samba or restarting the network has never worked for us.  And we have one computer that rarely appears on the network, yet all the configuration files are identical to the ones that work!  It can't even see itself half the time either.

Good Luck

TTUL
Gary

---

### Post by coojofresh on 2008-11-19
hey are you using the GUI?  i was having issues and i DL'd the Samba manager and i haven't had any issues. [http://us6.samba.org/samba/download/](http://us6.samba.org/samba/download/)

---

### Post by Thelasko on 2008-11-20
> **coojofresh said:**
> hey are you using the GUI?  i was having issues and i DL'd the Samba manager and i haven't had any issues. [http://us6.samba.org/samba/download/](http://us6.samba.org/samba/download/)

I use the [system-config-samba]("http://packages.ubuntu.com/hardy/system-config-samba") package for a GUI.

---

