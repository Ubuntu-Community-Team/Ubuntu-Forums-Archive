---
title: "Trying Ubuntu without Installing"
date: 2016-07-25
forum: New to Ubuntu
---

### Post by gauravgoenka on 2016-07-25
Hi Everyone,

I am new to Ubuntu. I am trying out Ubuntu (latest version) without installing it, from my bootable USB flash drive.

I am facing below issues while using Ubuntu:

1. I am not able to access any other external pen drive (and hard drive) while trying Ubuntu.

2. I am not able to install any browser plugin (like flash player).

Can you please help with the above issues. 

Thanks in Advance :)

Gaurav

---

### Post by mook765 on 2016-07-25
In a Live Session you are a bit restricted.
To access external drives they need to be mounted, they should appear on your desktop, rightclick them and choose mount.
If you are on a wlan, it might not work, it could need third party drivers to function properly., that would be solved in an installation.
Everything you change to the system will be lost, if you finish the Live Session as long as your Stick is not prepared with persistence.
if your stick is not prepared with persistence, you will not be able to make an y installations...
Give it a try and make a real installation...

---

### Post by mastablasta on 2016-07-25
> **gauravgoenka said:**
> 
2. I am not able to install any browser plugin (like flash player).


you need to install restricted extra package. Flash is there (at leats it used to be) along with other codecs. you can also use Google Chrome which comes with built in flash or install opensource Chromium and add pepper flash to it.

---

### Post by yancek on 2016-07-25
The Linux "Live CD" whether on a CD/DVD or flash drive uses an iso9660 filesystem which is read only and that can't be changed.  If you have enough RAM, you can install additional drivers/software or whatever.  Once you reboot, everything is lost.  That is by design.  I expect you are a windows user so you would be unfamiliar with the concept of a "Live CD" because nothing like that exists in the microsoft world.

---

### Post by grahammechanical on 2016-07-25
Ubuntu is Free and Open Source Software (FOSS). The Ubuntu ISO image does not included non-free, non-open source or proprietary software. Adobe Flash is proprietary software.

[https://en.wikipedia.org/wiki/Free_and_open-source_software](https://en.wikipedia.org/wiki/Free_and_open-source_software)

In a live session we can install proprietary software like Flash and audio & video codecs and also proprietary video drivers but once we shut down all that software is lost. It is not present the next time we load the live session.

When we install Ubuntu to the hard disk we are invited to tick a box labeled "Install third party software." That will install proprietary audio & video codecs and a proprietary video driver. I do not think that it will install Adobe Flash Player.

Adobe has not provided an up to date version of Flash for LInux for years. The Chrome web browser has the capability to handle Flash.

Regards.

---

### Post by gauravgoenka on 2016-08-02
Thank you so much for the replies.

The problem is that my hard drive has crashed and I am not able to boot anything from it. I am getting the Hard disk Quick 303 error. 
The computer repair person is asking for a lot of money to recover my data and says that I need to buy a new hard drive. As of now, I am short of cash. Thats why, for the time being, I was trying to use Ubuntu from a bootable flash drive just to surf the internet and work on my documents.
I am not able to mount any external drive (the pen drive/external hard drive) as it doesn't show up in my Ubuntu desktop and in Disks. 
I need to install flash plugin or Chrome browser for some video tutorials.

Can anyone please suggest what should I do?

Thanks in Advance

Gaurav

---

### Post by CatKiller on 2016-08-02
There is an option called Persistent Mode that will let you boot from your thumb drive and have your changes saved. If you want to install software and not have to redo it every boot, that's the way to go. You'll also be able to save changes to your documents that way, assuming you manage to get access to them in the first place.

---

### Post by gauravgoenka on 2016-08-23
Thanks. Can you please tell me, how to enable this Persistent Mode option?

---

### Post by mastablasta on 2016-08-24
when creating the USB for example from unetbootin or yumi or linuxliveUSb you can set the amount (size) of persistant file. say 2 Gb should be enough to add flash, codecs and a few other things.

---

