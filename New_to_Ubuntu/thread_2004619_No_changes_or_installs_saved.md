---
title: "No changes or installs saved?"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by johnnypict on 2012-06-16
Wondering if there is something obvious I need to do.

I have Ubuntu 12.04 running on a PC that dual boots with win7 

I have installed dropbox, ubuntu 1, chromium, flash player and when I reboot these packages need to be reinstalled.

Is there anything obvious I should know...totally new to Linux so a non techy explanation would be good.

Thanks in advance...

John

---

### Post by black veils on 2012-06-16
this may have no relevance:

open the **terminal**, type ```
groups username
``` replacing "username" with your username. press the **enter** key and post the results here.

---

### Post by Paqman on 2012-06-16
Are you running off a USB stick or CD, or have you installed it to the hard drive?

---

### Post by johnnypict on 2012-06-16
Hi both,

Installed on a dual boot hard drive with win 7.

Opened a terminal (after finding out what that was) and typed...

group username

Sorry edit used my username I got this back...
groups: anon: No such user
ubuntu@ubuntu:~$ ^C

Update:
I've just found out how to add a user. I've made myself admin...make any difference?




John

---

### Post by black veils on 2012-06-16
my guess from looking at that, is you are not running from your installation!  you are running from the live cd/usb.

otherwise, i have no clue.


Edit:

maybe to confirm, you should open **gparted** or **disk utility**, if the second app, then choose your harddrive from the left pane, and take a screenshot, post it here using the paperclip in your reply.

---

### Post by johnnypict on 2012-06-16
I am running the install off the PC (Used Unetbootin to dual boot) and to make sure I pulled out all the usb devices (had a usb hard drive with Ubuntu on it) and re started. 

Same issue and have covered the steps above again.

I've attached a screen shot as requested. 

Thanks,

John.

---

### Post by Paqman on 2012-06-16
> **johnnypict said:**
> I am running the install off the PC (Used Unetbootin to dual boot) and to make sure I pulled out all the usb devices (had a usb hard drive with Ubuntu on it) and re started. 

Same issue and have covered the steps above again.

I've attached a screen shot as requested. 

Thanks,

John.

Actually that picture shows you're not. Note the way your hard drive shows four partitions, all of them NTFS. That's a Windows filesystem. There is a way to install Ubuntu onto an NTFS filesystem called Wubi, did you use this when you ran the install?

Much more of a smoking gun is the fact that you've got a USB stick shown with "filesystem.squashfs". SquashFS is, well, a squashed filesystem, and is used on things like the LiveCD and LiveUSB.

So when you took that screenshot you were running from that USB stick. Now that you've pulled it out, reboot and assuming you used Wubi to install you should boot into your actual Ubuntu install instead of the Live USB.

---

### Post by black veils on 2012-06-16
this has really confused me. what exactly did you do to setup your claimed dual boot? and you say windows and ubuntu are on 2 different harddrives. 

we need one of those commands which lists all the drives and partitions... i haven't the time right now to find what that is. but you will need all operating system drives attached when you do get such a command.

---

### Post by Paqman on 2012-06-16
> **black veils said:**
> this has really confused me. what exactly did you do to setup your claimed dual boot? and you say windows and ubuntu are on 2 different harddrives. 

No, he's not mentioned a second hard drive, and Disk Utility only shows a single 1TB drive. You can see all storage devices listed down the left side of the window.

---

### Post by johnnypict on 2012-06-16
Ok Ubuntu is not running off a usb drive.
They are in the list but it is running off a hard drive that was partitioned using something called Unetbootin. This partitioned a hard drive that already has windows in it and it dual boots. That's the 1tb drive you see.

I think the issue may be that I may have installed Ubuntu with pen drive installer.
This being the case it would have the effect of looking like it is on a pen/usb drive would it not?

So I'll away and burn Ubuntu to a disk and start again and see what happens.

Thanks for your time, sorry if I've wasted any of it. 

Much appreciated, and I've learned something.

John.

---

### Post by Paqman on 2012-06-16
> **johnnypict said:**
> Ok Ubuntu is not running off a usb drive.
They are in the list but it is running off a hard drive that was partitioned using something called Unetbootin. This partitioned a hard drive that already has windows in it and it dual boots. That's the 1tb drive you see.


Right, unetbootin is actually a utility for creating bootable USB sticks that you can use to do the install. It doesn't in itself do any partitioning of your hard drive or install anything to it. The actual Ubuntu installer does that once you boot up into the USB stick and run it.

If you just ran Unetbootin you didn't actually install Ubuntu, you just set the USB stick up. When you rebooted it may have gone sraight to booting the Live USB system, which is what confused you. In Linux you can run a full version of the OS straight off the CD or USB before you've even installed it.

> I think the issue may be that I may have installed Ubuntu with pen drive installer.
This being the case it would have the effect of looking like it is on a pen/usb drive would it not?

Nope, it doesn't matter what install media you use, the end result is the same.

> 
So I'll away and burn Ubuntu to a disk and start again and see what happens.

You could just boot up into your USB stick and click the "install" icon on the desktop, it'll work the same.

> 
Thanks for your time, sorry if I've wasted any of it. 


Not at all. Helping people is what this forum is for. If you appreciate the time people have spent to help you, pay it back by spending some time helping other users.

---

