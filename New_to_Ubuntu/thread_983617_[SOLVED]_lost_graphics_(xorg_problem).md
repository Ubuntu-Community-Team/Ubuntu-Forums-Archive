---
title: "[SOLVED] lost graphics (xorg problem?)"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by zmike1 on 2008-11-15
I was trying to set up a second monitor for my dell inspiron 6400 laptop, running feisty with KDE and after either a restart (or maybe restarting X) I've apparently messed up my xorg server or something.

The system gives me no options and boots to the command line.  I'm totally lost so I'm now running from my original live CD.  

How do I recover what I used to have? I'll be happy just to have my GUI back and will work on the second monitor some other day.

---

### Post by benerivo on 2008-11-16
If you do```
sudo dpkg-reconfigure -phigh xserver-xorg
```it will give you a default setup. Your old xorg may have been overwritten, although it may have created a backup. Check in /etc/X11/ for a backup, and also see [this webpage]("http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/"). Firstly i would edit your current ('broken') xorg.conf by```
sudo nano /etc/X11/xorg.conf
```and look for some part of it which may refer to a dual monitor setup, and then comment out such lines with the # symbol.

---

### Post by zmike1 on 2008-11-16
Thank you.
Should I enter the command (sudo dpkg reconfigure...) now (while I'm running the live CD) or should I re-start with my broken system and then run it?

---

### Post by benerivo on 2008-11-16
Run the commands in the broken system.

You can use the live cd to look for any backups and replace the broken xorg.conf with them.

---

### Post by zmike1 on 2008-11-16
I tried the "sudo dpkg -reconfigure..." command and got an error:

"conflicting actions -e (--control) and -r (--remove)"

then some stuff that looked like it comes from a man page..?
I guess this is not expected...?
did I type something wrong?  I tried twice.

(thanks again for the help-- I have to run now but will be back)

---

### Post by MunkyJunky on 2008-11-16
Those messages are thrown up because the - shows the start of some triggers. Instead of picking up the keyword 'reconfigure', its trying to run with the triggers associated with -r, -e, -c, -o, ... etc. 

Are you putting a space between dpkg and -reconfigure? That may be your problem, I don't think there is supposed to be one.

---

### Post by zmike1 on 2008-11-16
Thank you MunkyJunky.  I did have the  extra space which was causing the problem.
I did the dpkg-reconfigure... and
Now the system starts to a gnome desktop instead of the KDE that was there before.  No big deal since I was thinking about changing anyway but I'm wondering how _that_ happened?

Also, since the live CD ran the graphics just fine, is there a way to copy the xorg.conf that it was using?

Thanks again for the help.

---

