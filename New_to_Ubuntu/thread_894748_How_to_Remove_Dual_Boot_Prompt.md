---
title: "How to Remove Dual Boot Prompt ?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by mithras93 on 2008-08-19
I have a new Dell Laptop that came with Vista (hate it).  

Tried to install Ubuntu--latest version, just downloaded--from disk.  Within Windows, I chose "Help me with Dual Boot" and then the Ubuntu prompt "Demo and Full Installation" and rebooted.

At the new dual boot prompt, I selected Ubuntu, and the laptop booted into the Ubunto Demo, which is all I wanted to look at.  However, my cursor would not work...it leaped all over the screen when I used the touchpad, and opened windows I did not intend to open.  I managed to shut down, and, assuming there is some sort of hardware issue, decided not to install the operating system.  I never actually chose to install Ubuntu.

Problem is, whenever I boot up, I'm still offered the dual boot option.  Can't get rid of it.  Tried system restore...no luck.

I see there is an Ubuntu directory on my C: drive now.  There is no Ubuntu program in the Remove Software window, not Ubuntu-related boot software.

So, my question is:  How do I get rid of the dual boot prompt when the computer starts up?

---

### Post by mithras93 on 2008-08-19
By the way, it's a Dell XPS...if that matters.

---

### Post by bobnutfield on 2008-08-19
You obviously were using WUBI.  In the Ubuntu directory there should be a folder with the option to uninstall (do not just delete the folder.)  Only tried WUBI once a good while ago, and that is how it worked for me.

---

### Post by mithras93 on 2008-08-19
Thanks for the response.  I scoured the directories.  There is no option (that I can find) for uninstalling.  I have not deleted the folder, or any of its contents.

---

### Post by bobnutfield on 2008-08-19
You should be able to find your answer here:

> [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by mithras93 on 2008-08-19
Thanks.  I went there and downloaded the installer.  It prompted me  to set a password, which I didn't have to do when I ran it from the Ubuntu disk I made from the ISO file.  So I ran that option from the disk again, and an option to uninstall Ubuntu did indeed appear this time in the Uninstall a program window.  And it did remove the Ubuntu folder and all the files...But the dual boot prompt STILL appears!  This is driving me nuts!

---

### Post by mithras93 on 2008-08-19
Solved the problem...found a program called EasyBCD, and it fixed the dual-boot issue.

Now, if I can just figure out how to get Ubuntu to work....

---

### Post by nicedude on 2008-08-19
To get Ubuntu to work instead of installing from within Windows with Wubi which isn't a dualboot at all. Try googling "Vista dualboot with Ubuntu" and read one the many guides out there for doing just that. Please just read up on this before doing it so you understand what you are doing and it will save you the headache of just trying it blindly and ending up with a messed up system.


Goodluck with the dualboot setup but don't worry it is not hard if you do your homework first :-)

---

### Post by Sunfist on 2008-08-19
If you really want to try Ubuntu dont get too discouraged from the Wubi install, I couldnt get that to work right on my computer either, but I repartitioned my HD and did a regular install of Linux and that worked fine. I know what you mean about Vista....thats a nightmare of an OS

---

