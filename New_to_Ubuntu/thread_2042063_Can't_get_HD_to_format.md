---
title: "Can't get HD to format"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by redham on 2012-08-13
Hi,

Really glad to be FINALLY making the switch to Linux. I'm trying "Ubuntu Desktop" but am open to suggestions for another type of Linux.

 I've had quite a hard time getting a install though and I'm still not quite there yet.

 I'm using an old P4 tower server to install my Linux onto. Problem is/was that it wants to boot straight to the CentOS that's on the installed hard drive. Even setting the bios to the CD as first boot device I couldn't get it to read from the CD (which has the Ubuntu Desktop install program). I have been fooling with that bios for hours (NO! ..... days!) and have only just now seen 'Ubuntu Desktop' on the monitor. Now I'm really ready to get it finished. ;=)

 Finally I simply unplugged the two hard drives and set it to boot from the USB. That got Ubuntu Desktop onto the monitor so now to install it to the hard drive is the next step. By the way, I can also boot from the CD ROM also now.

 Problem now is. When I plug in the hard drives I go right back to the old problem of booting to the old server OS (CentOS).

 I used my windows PC and a copy of Puppy to wipe one hard drive but when I boot into Ubuntu Desktop with that 'wiped drive' installed and try to "Install" Ubuntu Desktop onto the drive Linux isn't seeing it and I get an error:
that I don't have "4.4GB available disk space" for the required space for the Ubuntu Desktop install.

 Can someone please help me and tell me how I can see the 'wiped drive' from Ubuntu Desktop which is running from the CD ROM  (or USB) and format it or use it for the installation?

 I'm not familiar with Ubuntu Desktop and don't know how to make it see the drive.

 I've been at this for three nights now and I really do need an expert to guide me through this.

Thanks in advance,
Russ

---

### Post by Moose on 2012-08-13
Hi RedHam, I'm RedBacon ;) I know of a few good Linux Distro's. If you want something that is simalr to Mac OS X. It is called gOS. This one hasn't had a new realse for a while but the latest one realeased in '07 was pretty good. If you like the old Gnome shell try Fedora 16. Puppy Linux, Easy Peasy are good for Netbooks. Now for your problem. I am not quite sure why you are having this problem. Just try formmatting your biggest partition. Usually it is the one in the middle on the list. ( That is, if you haven't tried customizing your partitions.) After format just try installing it on that partition. 
 
[Edit] If you are trying to install to external harddrive then that is slightly more difficult because you need to create partition. Instructions can be found somewhere on the forums or on Ubuntu install instructions.
 
-Anarchy

---

### Post by Bucky Ball on 2012-08-13
What's on the wiped drive? Are there any partitions? If so, delete and try with free space.

When you are at the 'Try Ubuntu' desktop running from the CD open Gparted, the partition editor. What does it see that drive as and what does it say's on it?

I love Ubuntu but have been using Xubuntu version for ages now. Tried a couple of other distros but Xubuntu suits me best for now. Lighter and highly configurable. This community's a cracker which helps the decision also. ;)

---

### Post by redham on 2012-08-13
Hi,

So far I LOVE the quick support from the forums!

I THINK I got it. See if this is correct.

When I click "File System" This  is where I see everything that is on the "CentOS" old server drive.
I can simply DELETE these files and have plenty of room to install Ubuntu Desktop. Is this correct?

All files under "Home" are files on the CD and I need to leave those alone.

Russ

---

### Post by redham on 2012-08-13
P.S.

I know even less about the Mac OS than Linux so I'd be backing up. I have used Windows :-( forever now.
 I'm sick of it's crashes and bad support.

Russ

---

### Post by Bucky Ball on 2012-08-13
+1. You pretty much have got it. Use Gparted to do this while running from the CD. The partitions need to be unmounted to manipulate them so in Gparted, right click the partition you are about to delete and 'unmount' before deletion. 

You can then go on to install Ubuntu from the desktop icon. I personally go 'Something else' and set things up manually. If you do this, you might like to tweak things with a basic setup and mountpoints like this:

/ = root, the OS; I never need anymore than 15Gb (and don't actually need that).
/home = your personal data and settings - large as you like;
/swap = like pagefile in Win. 2Gb fine.

With a separate /home you can reinstall the OS without having to lose all your personal stuff. There are many ways to go about this but if you don't create a /home one will be created as directory in / (root partition). 

Good luck ... ;)

PS: These mountpoints used are all defaults available when you get to the manual partitioning section of the install.

---

### Post by Moose on 2012-08-13
RedHam if you are talking to me then i will rephrase what i said. gOS isn't identical to Mac OS X. i Looks like it, has a dock and the windows are similar. The Maximise, Minimise, Exit and search buttons are taken from a mac. Other than the cosmetic values of gOS it is just like any other Linux OS. So you can use gOS and enjoy they beauty of MAC OS X without having to put up with the traumatic abuse that is Mac :] gOS is based on Ubuntu but given a OS X twist. Hope i cleared it uo for you without causing offence. 
 
Sincerely, -Anarchy

---

### Post by redham on 2012-08-13
Hi,

Here is what happens when I try to use Gparted. 

When I'm logged into Ubuntu Desktop (CDROM) and invoke Gparted it ONLY shows the files on the CDROM. I can even try to do refresh and it still doesn't show the hard drive.

 I can change the file system to the hard drive and search for Gparted and it shows many copies of it. Like one for every file system on the hard drive.

 The "root" partition is by far the largest (978MB) but I don't have "permissions" to enter it. This makes me think that I won't be able to delete it either.

 Is there anyway to use the Gparted from the CD ROM to access the hard drive?
 This also could be a problem with the bios settings since I have made soooo many changes in them. I'm afraid to go back into it fearing I won't be able to boot back into Ubuntu Desktop.

Also, remember that i am using "Ubuntu Desktop" and not Puppy. Would loading Puppy instead help?

Thank you for helping me.
Russ

---

### Post by redham on 2012-08-13
Anarchy,

No, no offence taken what so ever. I was just saying that it wouldn't help as far as my learning curve with Linux.

Actually I'm glad to be on this learning experience. I'm so fed up with Windows and the latest windows sidebar abandonment was the straw that broke this camel's back.

Thanks you for your suggestion and be sure that Ill be trying more than just the '' version of Linux.

Thanks,
Russ

> **AnarchyTech said:**
> RedHam if you are talking to me then i will rephrase what i said. gOS isn't identical to Mac OS X. i Looks like it, has a dock and the windows are similar. The Maximise, Minimise, Exit and search buttons are taken from a mac. Other than the cosmetic values of gOS it is just like any other Linux OS. So you can use gOS and enjoy they beauty of MAC OS X without having to put up with the traumatic abuse that is Mac :] gOS is based on Ubuntu but given a OS X twist. Hope i cleared it uo for you without causing offence. 
 
Sincerely, -Anarchy

---

### Post by Bashing-om on 2012-08-13
a quick note and I will get out ...
as to using Gparted: in the upper right corner of the application will see your devices that Gparted is aware of ..I expect you will see sda (hda on older ide drives), to the right of "sda" will have a upside down pyramid icon. this will allow to access other disk devices on your system. will see how the devices are set up in the large display area.  Find the device you think you have wiped.
while the wiped device is selected ,from the tool bar choose device and
and format ...will come up to format as msdos ... that is good ,this format is not what you might think (MicroSoft Dos)... if you use this option it will insure the disk partition table is erased.

[INDENT]hth 
[/INDENT]

---

### Post by Bucky Ball on 2012-08-14
Yea, drop down list in top corner of Gparted. Should have all drives listed when you click, including any usb/esata/firewire external drives/dongles.

---

### Post by redham on 2012-08-14
Hi Guys,

Thanks for your help.

After going back into bios I have the 'Ubuntu Desktop' loading onto my hard drive at this moment.


Thanks for your quick replies and help.

I'm on well on my way to becoming a new Linux user!

Thanks-A-Bunch,
Russ

---

### Post by Bucky Ball on 2012-08-14
Great news! Enjoy the learning curve and the OS. Please mark thread as 'Solved' by using 'Thread Tools' to help others.

Post back on a new thread with any further issues, probs, comments. ;)

---

