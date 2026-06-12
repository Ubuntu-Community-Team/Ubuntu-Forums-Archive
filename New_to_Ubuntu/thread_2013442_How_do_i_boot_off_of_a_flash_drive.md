---
title: "How do i boot off of a flash drive"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by Lang901 on 2012-06-30
So, I am trying to boot another ubuntu based OS called [debateOS]("http://debateos.org/") and I don't want to delete my data off of my hard drive.  So, I have heard that you can put this OS on to a flash drive but I'm sadly a noob at this, so I was wondering if anyone could give me some help.  I am using an Inspirion 1501 running XP service pack 3.

---

### Post by afz12 on 2012-06-30
Hi Lang901

I have done this before with a notebook. I saved the Ubuntu ISO image to a USB drive as per the instructions on the download site (or USB stick). I then booted the notebook with it inserted and changed the BIOS order to place the boot USB drive first in the boot list (pressing "esc key" during boot up on this notebook). This made the notebook ignore its internal hard drive and run directly from the external USB drive - a bit slower but still OK. However things can easily go wrong so I suggest you make comprehensive backups first!

---

### Post by flemur13013 on 2012-06-30
This thread has links in it (2nd post):

[http://ubuntuforums.org/showthread.php?t=2012269](http://ubuntuforums.org/showthread.php?t=2012269)

---

### Post by robtygart on 2012-06-30
> **Lang901 said:**
> So, I am trying to boot another ubuntu based OS called [debateOS]("http://debateos.org/") and I don't want to delete my data off of my hard drive.  So, I have heard that you can put this OS on to a flash drive but I'm sadly a noob at this, so I was wondering if anyone could give me some help.  I am using an Inspirion 1501 running XP service pack 3.

Have you looked at VirtualBox? You can try out an operating system from your current system. It will be in your software center. 

Here is the site for more info [https://www.virtualbox.org/](https://www.virtualbox.org/)

[IMG]https://www.virtualbox.org/raw-attachment/wiki/Screenshots/gnome.png[/IMG]
[Photo Link]("https://www.virtualbox.org/attachment/wiki/Screenshots/gnome.png")

---

### Post by Shadius on 2012-06-30
> **Lang901 said:**
> So, I am trying to boot another ubuntu based OS called [debateOS]("http://debateos.org/") and I don't want to delete my data off of my hard drive.  So, I have heard that you can put this OS on to a flash drive but I'm sadly a noob at this, so I was wondering if anyone could give me some help.  I am using an Inspirion 1501 running XP service pack 3.

Once you've downloaded the image of the operating system, put it on a USB flash drive. Now to get your system to boot from the USB flash drive, go into the BIOS (either by pressing F2, Delete, or some other key while your system is starting up), then once you're in the BIOS, you must change the boot order so that your USB is the first on the list, then save the changes you've made and reboot. Once the USB flash drive is connected, your computer will boot from the USB flash drive. 

Here's some helpful information about the BIOS for you: [BIOS]("http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm")

Let me know if you need further help.

---

### Post by Lang901 on 2012-07-01
Thank you for all the help, unfortunately the screen for my laptop had a backlight issue and is being repaired and should be done tomorrow(Monday) so tomorrow will be an interesting day.

---

