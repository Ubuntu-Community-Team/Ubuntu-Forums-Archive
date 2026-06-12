---
title: "Boot up from Memory Stick"
date: 2020-11-13
forum: New to Ubuntu
---

### Post by gmseed on 2020-11-13
They make it sound so easy:

[https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive](https://ubuntu.com/tutorials/install-ubuntu-desktop#4-boot-from-usb-flash-drive)

I downloaded and placed on a memory stick Ubuntu Desktop, 20.04LTS. The memory stick consists of the single file "ubuntu-20.04.1-desktop-amd64.iso"

Apparently, I insert a memory stick in my laptop, hold down F12 as the machine boots up and I'm away. Yeah - right!

I have a Sony VAIO VPCEC3SOE and F12 appears NOT to work.

I found a YouTube video which suggests holding down F11, which I did. I then got a message "Missing Operating System".

I currently have Ubuntu 17.04LTS installed and wanting to upgrade.

Does anyone know how this is achieved?

Thanks.

---

### Post by CelticWarrior on 2020-11-13
> **gmseed said:**
> 
I downloaded and placed on a memory stick Ubuntu Desktop, 20.04LTS. The memory stick consists of the single file "ubuntu-20.04.1-desktop-amd64.iso"


It is easy with a properly done USB installation media, not the way you did. I wonder how have you managed to install Ubuntu before?
[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)

---

### Post by gmseed on 2020-11-13
I previously installed it via a CD/DVD.

This time I wanted to try a memory stick.

The link I provided is the installation guide on how to install a new version of Ubuntu from a memory stick.

Let's step through what a new user sees:

1) [https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#download](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#download)

This is the download page. At the bottom left is a link "Installation Guides for ...". Click this link.

2) [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

This page states: "In this tutorial, we&#8217;re going to install Ubuntu desktop onto your computer, using either your computer&#8217;s DVD drive or a USB flash drive."

Now we step through the 11 steps, and specifically Step 4 on installing from a memory stick or flash drive as they refer to it.

3) Now, tell me what I did wrong in following their steps to the letter.

Their own installation guide <snip> requires a new user to access another page NOT specified in this guide.

---

### Post by tea for one on 2020-11-13
From [https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Step Two - Requirements > [COLOR="#0000FF"]Several Tutorials[/COLOR] takes you to [https://ubuntu.com/tutorials?topic=desktop](https://ubuntu.com/tutorials?topic=desktop)

Scroll down to [COLOR="#0000FF"]Create a Bootable USB [/COLOR] (either Windows or Ubuntu)

---

### Post by gmseed on 2020-11-13
Thanks, but I do NOT want to create a bootable USB but a new laptop installation from a usb using the .iso file as indicated.

This is what the installation guide states:

"In this tutorial, we&#8217;re going to install Ubuntu desktop onto your computer, using either your computer&#8217;s DVD drive or a USB flash drive."

I am trying to follow their own guide to the letter to show what rubbish it is.

---

### Post by tea for one on 2020-11-13
> **gmseed said:**
> I currently have Ubuntu 17.04LTS installed and wanting to upgrade.

Does anyone know how this is achieved?

Thanks.

There is no direct path to upgrade from 17.04 to 20.04 because 17.04 has reached EOL (End of Life)

A fresh install is required.

Therefore, you will have to make a Bootable DVD or USB.

---

### Post by gmseed on 2020-11-13
All that is required in Step 4 of the Installation Guide is wording to the effect:

"In order to install Ubuntu using a USB memory stick/flash-drive you first need to create a USB bootable disk ..."

The installation guide gives the impression that an installation can be performed using a USB stick via an .iso file in the same way as a DVD media drive, which is not the case.

If a new user follows the steps verbatim then they are confusing.

---

### Post by sudodus on 2020-11-13
1. Please realize that we, the people who help users here, are only volunteers, and we do not own/edit the Ubuntu web page that you are referring to.

2. But I think that the information on that page and its sub-pages is useful for most users.

[hr][/hr]
Anyway, we can help you create a working USB boot drive using other instructions, if you wish. See for example the following link and links from it,

[help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There are also other links, that you may prefer. Good luck and please let us know, if you want other links/methods :-)

---

### Post by gmseed on 2020-11-13
"...useful for most users..."

It is the Installation page for goodness sake!! Probably one of the most important pages to attract new users, and a new user gets to Step 4 and is baffled by very poorly written support documentation. A new user goes from Step 3 to Step 4 under the impression that a usb memory stick bootable device is not required. In my humble opinion Step 4 needs a rewrite, but like much of software documentation it is written by people who couldn't talk their way out of a paper bag.

Those 11 steps should be fool and dummy proof.

---

### Post by sudodus on 2020-11-13
You may be able to get the attention of the Ubuntu developers, if you create a thread, 'new topic', at the following web page,

[Ubuntu Discourse](https://discourse.ubuntu.com/)

---

### Post by ActionParsnip on 2020-11-13
Use Etcher or Rufus to put the ISO on the USB stick. Just copying the ISO as a single file doesn't work

---

### Post by yancek on 2020-11-13
The information in the link in your first post explains how to "install" Ubuntu from a DVD or USB but does not tell you how to create a bootable usb.  It is possible to boot the Ubuntu iso file directly from the USB since you already have Ubuntu and Grub installed on your internal drive.  You would need to create a proper boot menuentry in the grub.cfg file of Ubuntu 17.04.  In order to do that you would need to know on which drive and partition the iso file resides.  Below is an example entry which shows on the 'set root' line the iso is on the 2nd drive (hd1) and the 3rd partition (gpt3) of a gpt drive.  You would need to change the drive and partitions to suit your system, also is it a gpt or msdos drive.  Won't work if you have the wrong entry.  The name of the iso must be exactly as it is on the USB.  If you want to try this entry,  copy and paste the entry to grub.cfg on 17.04 and then make the necessary changes.  Save the changes but do not run update grub.

>  menuentry "Ubuntu 20.04" {
set root='hd1,gpt3'
loopback loop /ubuntu-20.04-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-20.04-desktop-amd64.iso quiet splash --
initrd (loop)/casper/initrd
} 

---

### Post by MartyBuntu on 2020-11-13
You know which Ubuntu documentation *is not* poorly written?
The documentation explaining the life cycle and upgrade necessity of non-LTS Ubuntu releases.
As a matter of fact I'd say it's foolproof.

---

### Post by jim Kane on 2020-11-13
In fairness this page is for Absolute Beginners 
on the "tutorials/install" page step 4 it says "Most computers will boot from USB automatically" 
but a lot will Not and it gives no advice that you may need to make the USB stick Bootable or how to do do that

---

### Post by MartyBuntu on 2020-11-13
> **jim Kane said:**
> In fairness this page is for Absolute Beginners 
on the "tutorials/install" page step 4 it says "Most computers will boot from USB automatically" 
but a lot will Not and it gives no advice that you may need to make the USB stick Bootable or how to do do that

The author of this thread is trying to do an in-place upgrade and is interpreting the terms "install" and "installation" as a means to do just that.
Trying to upgrade a non-LTS release, years after end-of-life support doesn't help the matter.

---

### Post by C.S.Cameron on 2020-11-13
For making a basic installation USB it is simplest to clone the ISO file to the USB as a ISO9660 partition.

There are many tools that will do this including Etcher, (for Windows and Linux), Startup Disk Creator, (included on the Ubuntu install), Gnome-Disks, (also included with Ubuntu installs), dd can be used in Terminal, (but is more for experts), UNetbootin,  (for Windows and Linux), and mkusb which first needs to be installed in Ubuntu.

If you have a running Ubuntu system, Startup Disk Creator, is probably your best bet.

Once you have a working Ubuntu Live installer, proceed exactly like you did using a Live DVD. or proceed with the method in your link.

---

### Post by MartyBuntu on 2020-11-13
They want an upgrade, not a new install.

They're confusing the term "install" meaning "install the latest version on an already running operating system".


*...and please...nobody should be giving instructions on upgrading incrementally through step-by-step repository changes....if anyone has that idea. It would be a disservice, to put it mildly.*

---

### Post by DuckHook on 2020-11-14
The OP has left the building so thread has been closed to prevent our volunteers from wasting any more time on this issue.

Thanks everyone!

---

