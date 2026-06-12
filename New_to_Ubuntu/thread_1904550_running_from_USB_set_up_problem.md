---
title: "running from USB set up problem"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by OhKookoo on 2012-01-04
Hi! I'm new to this forum, and Ubuntu.

I am trying to learn by running v 11.xx from my USB instead of installing to my pc running Win 7.

My "problem" is that many of my settings are not being saved.  Bookmarks in Firefox, Mail accounts and settings in mail, etc.  And, stuff I have downloaded.

So, how do I "set up" my Ubuntu so that it saves "stuff" to the USB flash drive it is running from?

Is it likely the previous downloads, etc are saved somewhere on my PV hardrive, even though I booted and run from the usb drive, and if so, where?

Thanks for the anticipated acceptance and help.

I really want to eventually migrate to ubuntu from win 7, but not before I'm totally comfortable.

---

### Post by wildmanne39 on 2012-01-04
Hi, no it did not save them to the hard drive.

When you created your liveusb did you make it persistent? and what did you use to create it?
Thanks

---

### Post by Basher101 on 2012-01-05
> **wildmanne39 said:**
> Hi, no it did not save them to the hard drive.

When you created your liveusb did you make it persistent? and what did you use to create it?
Thanks

from what i can read he did not set up any persistence.

Persistence is some additional space on your USB where exactly those settings can be saved to. But you must set that up with the program you used to make the Live USB (i guess you used Universal-Usb-Installer version 1.8.6 ?)

---

### Post by wildmanne39 on 2012-01-05
Hi Basher101 that is my guess too, I have only used startup disk creator in ubuntu to make a persistent liveusb.
Thanks

---

### Post by C.S.Cameron on 2012-01-05
Usb-creator offers a persistence option with a maximum persistence file size of 4GB.
If you need more space you can create ext4 partitions named casper-rw (and home-rw, if you want a separate home partition).
With a persistent flash drive you should never do an update using update manager, it can make the drive unbootable.

---

### Post by OhKookoo on 2012-01-05
I downloaded the software from [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)  and "created" a USB stick for windows 7.  The ubuntu version is 11.10  Than I downloaded this:                  [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)  to create the USB drive.


My laptop automatically boots from the usb after I changed the sequence in my bios.



I have used it several times and so far like it.  BUT, would like to know what I need to do to save stuff to the USB.

I do not want to save on my computer, afraid I may cause myself problems.  Do not want to create a dual boot system. I'm pretty happy being able to run it from the USB, and to be able to take it with me anywhere.

So, what do I need to do to save that "stuff" to the USB?  It's 32 gb, so plenty of storage, I think. :)

Should I download the "persistence", and if so from where?
Will than allow me to use all 32 gb on the usb drive I'm using, or should I use something smaller, perhaps 4 gb or 8 gb?  ( I have a drawer full, so to speak.)

thanks for the speedy responses!

---

### Post by OhKookoo on 2012-01-05
I just looked at the "easy 1-2-3" program that I used to download and create the usb drive. I would have accepted the default settings, which show a persistent drive. 

[IMG]http://www.pendrivelinux.com/wp-content/uploads/Universal-USB-Installer.png[/IMG]

The image shows mythununtu 10.10. I definitely installed ubuntu 11.10.  No doubt about that.  

So, do I start again from scratch, or what?

thanks!!

---

### Post by C.S.Cameron on 2012-01-05
Plug your flash drive into a computer running Windows or Linux.
Check if there is a file in the root directory named casper-rw.

casper-rw is the persistence file where stuff is saved.

If casper-rw is not there then the persistent install failed.

I prefer to use usb-creator which comes with Ubuntu.

You can install to usb using the Live CD, go to System/Administration/Startup Disk Creator.

or you can extract usb-creator.exe from the iso to use in windows

---

### Post by OhKookoo on 2012-01-05
Thanks. I think. :)
I did not find a "root" directory. I have folders named: .disk, boot, casper, dists, install, pics, pool, preseed, syslinux.  I opened each and did not find "casper rw".

So I figure I'll just download everything again, and start from scratch.  Since I'm just beginning to learnm, am I going to be wasting usb space with the 32 gb? Would I be better off using an 8 gb or 4 gb usb pen drive?  should I use the "easy 1-2-3" again, or something else, and if something else, where do I find it?

And should I "accept" the defaults for the persistent thing?

thanks

---

### Post by Basher101 on 2012-01-05
you would be wasting space if you do not use it...thus you have enough space to make a full install on the USB (i wanted to do the same for a portable Ubuntu, but a 32 GB USB stick was 35 € and right next to it was a box with an external HDD with 320 GB for 40 €...so i told myself "5 bucks more for 10x the space...sounds about right" and i bought the external usb hdd. tru story :D 

anyways you should make a full installation on it, you would use 4 GB persistence anyway and thats as much as the full install will take.

you can get more Live USB creation programs here at [http://www.pendrivelinux.com](http://www.pendrivelinux.com)


regards

---

### Post by OhKookoo on 2012-01-05
At this point, I think I'd be happy if the install remembered my wifi network key, bookmarks, and emails, some other "apps" and plug ins for my browsers.  

So I'll downsize the usb drive and use a 4 gb while I "learn" the system.  Been a pc & windows user since the early days of DOS, and don't have much of a clue about other OS's.

thanks again.

---

### Post by Basher101 on 2012-01-05
> **OhKookoo said:**
> At this point, I think I'd be happy if the install remembered my wifi network key, bookmarks, and emails, some other "apps" and plug ins for my browsers.  

So I'll downsize the usb drive and use a 4 gb while I "learn" the system.  Been a pc & windows user since the early days of DOS, and don't have much of a clue about other OS's.

thanks again.

well then its time to discover the wide, vibrant an adventurous Open Source world! :D

---

### Post by OhKookoo on 2012-01-06
I'd like to say THANK YOU to everyone.

I made a new 4gb USB with the persistent drive, and now have my surfing stuff and will be using Ubuntu to begin my learning process.

So, this thread has helped me immensely, and should not be considered "solved" or closed, and I will if I can figure out how. 

:))

---

