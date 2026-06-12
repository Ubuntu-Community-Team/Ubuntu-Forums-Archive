---
title: "What Parallels can I use to install Windows in Ubuntu 8.04?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by rialto on 2008-04-30
Hi! I was wondering how can I install windows within Ubuntu 8.04? Not dual boot but like a parallel program similar to VMware Fusion for Mac OSX.  What program can I use? and where can I get it?

Also, I'm a beginner regarding this so a step by step howto would be great!

---

### Post by eriqjaffe on 2008-04-30
IIRC, Virtualbox has a "seamless" mode which I think may be what you're looking for.

If it's just for one or two applications, you may be able to get away with Wine...

---

### Post by ugm6hr on 2008-04-30
Try 1 of the stickies here:
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by SlappyPappy on 2008-04-30
I'm using Virtualbox and running Windows 2000 and loving it. 

Couple of tips that will save you hours of hassle that I went through this last weekend. Do NOT get the OSE or Open Source Edition of Virtualbox. It's crippled in comparison to the PUEL edition. Also, get the latest version of Virtualbox from the Innotek website, the version that is in Synaptic will just give you headaches, it did for me.

Next, make sure you download the Guest Additions after you install Windows. This enables sharing of folders between guest and host, USB, better graphic card, etc.

To get USB up and running so sweetly check out this link:

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

Follow that and you will be good to go. Worked a treat for me.

Then to get a printer going:

[http://forums.virtualbox.org/viewtopic.php?t=1465&highlight=usb+printer](http://forums.virtualbox.org/viewtopic.php?t=1465&highlight=usb+printer)

It's super simple to do and makes so much sense printer-wise.

Then just smile and laugh as your Windows install runs so sweetly inside of Linux!  :)

---

### Post by wahoobob on 2008-05-02
> **SlappyPappy said:**
> I'm using Virtualbox and running Windows 2000 and loving it. 

Couple of tips that will save you hours of hassle that I went through this last weekend. Do NOT get the OSE or Open Source Edition of Virtualbox. It's crippled in comparison to the PUEL edition. Also, get the latest version of Virtualbox from the Innotek website, the version that is in Synaptic will just give you headaches, it did for me.

Next, make sure you download the Guest Additions after you install Windows. This enables sharing of folders between guest and host, USB, better graphic card, etc.

To get USB up and running so sweetly check out this link:

[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

Follow that and you will be good to go. Worked a treat for me.

Then to get a printer going:

[http://forums.virtualbox.org/viewtopic.php?t=1465&highlight=usb+printer](http://forums.virtualbox.org/viewtopic.php?t=1465&highlight=usb+printer)

It's super simple to do and makes so much sense printer-wise.

Then just smile and laugh as your Windows install runs so sweetly inside of Linux!  :)
I just downloaded and installed the OSE VirtualBox and it won't let me get to some shared folders easily.  Is there a way to share the main folders on my harddrive?  Also, you mentioned the PUEL VirtualBox and when I go to the site to try and download that I get sent to the OSE version.  Where do I obtain the PUEL version for 8.04?  Thanks for your help, in advance.  I think virtualbox will allow me to get rid of the Windows partition since all I use there is Family Tree Maker and an occasional need for IE when the boss wants me to take a tutorial that demands it.

---

### Post by rialto on 2008-05-02
after a couple of days trying to figure out OSE because I had installed it through automatic add/remove function, I finally called it quits and followed Slappypappy's advise.  I downloaded virtualbox straight from the sunmicrosystem's website and the install was pretty much automatic.  Getting everything up and working so much easier!!!  Thanks so much Slappypappy!

Also, I used this thread to help me with my install.

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

I'm still trying to figure out how to get the mouse working because it keeps saying that I have to capture and when I do use capture, it won't let me use the mouse within that window.  Rather it told me something about guest additions.  I'm not sure what that is, but i'm still figuring it out.  

edit: I've also tried to install through devices>install guest additions

When i do this, nothing pops up and nothing happens.

Any help?

---

