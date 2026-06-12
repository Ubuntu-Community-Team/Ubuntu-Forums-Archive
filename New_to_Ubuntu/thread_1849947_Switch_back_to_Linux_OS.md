---
title: "Switch back to Linux OS"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by QuentinK on 2011-09-25
A few weeks ago, I wiped my HDD and installed Ubuntu 11.04 onto it as the main OS. Then recently (a few days ago) I partitioned about 15 gigs of the HDD, and installed Windows 7 onto it. Obviously Windows took the obligation of making itself the boot OS, which was fine at the time, since with all the programs and settings I had to install, a lot of restarting took place. 

However, I need to go back to Ubuntu (since most of the HDD is Ubuntu). I figured I could just F8 during Bootup to select the OS, but it just gave me W7 recovery options, so I tried to change the OS within W7 itself, but Ubuntu wasn't under the OS choices. 

Is there anyway to get back to Ubuntu, possibly through the flashdrive I used to install it in the beginning?


Much appreciated to whomever can help.

---

### Post by Elfy on 2011-09-25
reinstall grub

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by QuentinK on 2011-09-25
I tried to install GRUB from my LiveCD, but it's not showing the filesystem that my Ubuntu is on under the "Places" menu. It shows the 15g filesystem for Windows, but not the 55g filesystem for Ubuntu, and when I try to use the terminal way to install GRUB, it says something about installing on a partionless disk and it's bad idea.

And when I just try to install Boot-Repair, I get a 404 error when installing the repo.

---

### Post by BeRoot ReBoot on 2011-09-25
Does your ubuntu partition show up in gParted? If not, you've probably accidentally deleted it. If it does, and this turns out to be a deficiency in Ubuntu's grub tool, you may want to try installing grub with [Super Grub Disk]("http://www.supergrubdisk.org/") instead.

---

### Post by QuentinK on 2011-09-25
After a reboot I was able to access the filesystem, and I installed GRUB, and restarted my computer, and it took me back to my Ubuntu, but now I feel I'm in the reverse situation, I can't get back to Windows.

---

### Post by BeRoot ReBoot on 2011-09-25
Wait, do you even have a separate /boot partition?

---

### Post by QuentinK on 2011-09-25
What?
Do you mean a separate partition for Ubuntu and Windows? Yes I do.

---

### Post by candtalan on 2011-09-25
I used this boot repair disc and I was surprised at how easy, non techy and just magic, it was!
[http://sourceforge.net/projects/boot-repair-cd](http://sourceforge.net/projects/boot-repair-cd)

---

### Post by QuentinK on 2011-09-25
Well some odd string of events happened, which ended up with me being able to get back to Ubuntu and install boot-repair, which, for some reason, LiveCD couldn't do. Now GRUB works and it gave me the option to switch OS's.
I'm confused, but content.

---

### Post by ClientAlive on 2011-09-25
> **QuentinK said:**
> What?
Do you mean a separate partition for Ubuntu and Windows? Yes I do.


It is possible to create separate partitions within the linix installation and put different components of the system in different partitions - but I'm not entirely familiar with the 'why' details. I know the how, just not the why.

I hope this is not off-track but I found a link that may help. If you read a few posts through you see that they also talk about possible problems because the guy asking about it seemed to want to do things a little differently than the usual. One post, by a user named "Herman" and dated: January 20th, 2009, 02:57 PM (to help you identify which post) seems to have a good general explanation - especially in the last paragraph.

> A 'Dedicated GRUB Partition', is a partition that contains only GRUB files, and is operating system independant. This is the kind of GRUB partition that's great for anyone who likes GRUB, and wants to multi-boot. A 'Dedicated GRUB partition can be anywhere in a hard disk, and doesn't take up very much room at all.
 The term 'Dedicated GRUB Partition', was probably coined by the web author Steve Litt, in his article ' Making a Dedicated Grub Partition ([http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm))'.


Link: [http://ubuntuforums.org/archive/index.php/t-1045237.html](http://ubuntuforums.org/archive/index.php/t-1045237.html)

HIH

;)
---------------------

Edit:

If you like, here are a couple links that are pretty informative as well.

~ How a boot loader works and how the computer starts up (easy read and very detailed):

[http://lennartb.home.xs4all.nl/bootloaders/node3.html](http://lennartb.home.xs4all.nl/bootloaders/node3.html)

~ Older but very technical and comprehensive (lots of great, nitty gritty, stuff):

[http://www.mossywell.com/boot-sequence/](http://www.mossywell.com/boot-sequence/)

Hope you enjoy Ubuntu. Welcome aboard!

:popcorn:

---

### Post by BeRoot ReBoot on 2011-09-25
> **ClientAlive said:**
> It is possible to create separate partitions within the linix installation but I'm not entirely familiar with the why details. I know the how, just not the why.

So threads like this don't happen. /boot is a separate partition where the bootloader is installed, safe from the windows bootloader, which installs in the MBR.

---

### Post by pkg9991 on 2011-09-25
from the Live CD of the OS enter the recovery mode and from there check for boot status

---

### Post by ClientAlive on 2011-09-25
> **BeRoot ReBoot said:**
> So threads like this don't happen. /boot is a separate partition where the bootloader is installed, safe from the windows bootloader, which installs in the MBR.


Yeah, I think that's what Herman begins to clarify as the thread moves on. It isn't long before they say what you just did - pretty much.

---

