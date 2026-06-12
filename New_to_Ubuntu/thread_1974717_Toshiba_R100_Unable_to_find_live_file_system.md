---
title: "Toshiba R100 Unable to find live file system"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by Porsche650 on 2012-05-06
I have a Toshiba Portege R100 and I am trying to install just Ubuntu on it.  The computer has a usb floppy and a PCI card cd-rom also I have not been able to get a usb stick to boot ubuntu.  

I have made copies of ubuntu 10.10,9.04,8.04 and tried installing using those cd's but I end up getting an error Unable to find a medium containing a live file system.

I have also formatted the computer using NTFS for linux.

I have been trying to install XP to see what the problem may be, I can't boot from cd or else I get a blue screen error. Install XP i have to use the recovery disk and boot with them and that will mount the cdrom giving me an X: drive(cd-rom) and ram drive D:(tools) and by using X: cd I386 then winnt it copies files to my C: drive and installs.  I am guessing Ubuntu is not mounting the cd-rom and thats why so is there anyway to install files to drive or mount the cdrom using command?  I have tried a few sudo mount/dev/ commands and no luck

At the moment I would perfer the computer to just have UBUNTU no windows.

---

### Post by gordintoronto on 2012-05-06
How much memory on that puppy? You're trying to install obsolete versions of Ubuntu, so those are not great choices. I suggest the current Lubuntu unless the laptop has extra memory over the base 256 MB.

How did you create the CDs? Do you understand the phrase "burn the image"?

I could be wrong, but I don't think you can install any Ubuntu variant on NTFS. During installation you can choose EXT3 or EXT4.

---

### Post by Porsche650 on 2012-05-06
Memory is 512.  

"You're trying to install obsolete versions of Ubuntu, so those are not  great choices. I suggest the current Lubuntu unless the laptop has extra  memory over the base 256 MB."

Sorry I am new to linux Lubuntu isen't this basically the same thing just newer? 
Being that the computer was older I tried using a older version to see if it would install any better since there are a few google searches for R100 ubuntu 9.04.
Even if I put the newest version on the computer I don't believe it would get past my error.

"How did you create the CDs? Do you understand the phrase "burn the image"?"

Yes I do I use nero for my burning purposes, and yes I understand Burn the image the iso file.

"I could be wrong, but I don't think you can install any Ubuntu variant on NTFS. During installation you can choose EXT3 or EXT4."

I checked and it seems like you can but it will affect the performance.

Nice article on it [http://www.pcworld.com/businesscenter/article/230527/ubuntu_linux_day_16_ext4_vs_ntfs.html](http://www.pcworld.com/businesscenter/article/230527/ubuntu_linux_day_16_ext4_vs_ntfs.html)

---

### Post by Porsche650 on 2012-05-06
I just tried using EXT4 and I get the same thing.

---

### Post by gordintoronto on 2012-05-07
So you get to the point of specifying partitioning for the hard drive?

When/where does the message appear?

---

### Post by Porsche650 on 2012-05-07
using ubuntu 11.04 it starts loading screen with an icon on the bottom right before it asks you next or to pick anything, the screen goes black and when i hit a random key i see the error.  With the older versions it loads the start up screen where I put ENGLISH then Install Ubuntu then I get a black screen again and get the error.

---

### Post by gordintoronto on 2012-05-09
If it were my system, I would try Lubuntu 12.04, and "nomodeset".

Hold shift from the BIOS boot to get a Grub menu. Press "e" on getting the Grub menu. Using the arrow keys, navigate to, and delete, quiet and splash and type the word nomodeset in their place. Press Ctrl-x to boot.

---

### Post by Porsche650 on 2012-05-14
Sorry for the late response I haven't had time for anything this week I will try Lubuntu and let you know.

---

### Post by Porsche650 on 2012-05-14
When I press Shift during boot the screen comes to Boot: then when e is pressed or with shift e it saids Boot: if anything inputed it saids Could not find kernel image:

Trying to install it saids the same as Ubuntu

---

### Post by gordintoronto on 2012-05-15
You have a bad CD, or a hardware problem.

---

### Post by Porsche650 on 2012-05-16
I burned the cd very slow as I saw many people were having problems with cd's being burnt too fast.  In terms of hardware failure I did a memory test memtest86 i believe is the software and I used the supplied cd mem. test.  Also the hard rive is brand new the other one died before I started doing all these attempts at installs.  Also the computer was given to me from a friend and the motherboard was replaced by a genuine motherboard 2 years ago so what else could it be?

If I can install XP by copying the I386 files to C: would i be able to do the same with this?

Could the actual cd rom be the problem it is the PCI card type?

I would get a USB but I doubt it would boot up in USB or else I would use a USB stick

---

### Post by Cheesemill on 2012-05-16
If you have another machine that you can plug the HD into then you can use that to do the installation.

Just plug the laptop HD into the other machine making sure it is the only HD attached, run the installer, and then switch the drive back into your laptop.

---

### Post by Porsche650 on 2012-05-16
I actually did buy an adapter but was worried to use it, the 50 pin side of the adapter has no position for the hard drive and the laptop has one oval pin and one circle on the which matches the hard drive.  The other side is an IDE connector and a power connector have a guide.  When I put the hard drive in either position one does nothing and the other powers the drive on and off.  I see they sell USB cd roms would that be something to try?

---

