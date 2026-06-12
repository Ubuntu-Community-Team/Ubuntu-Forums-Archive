---
title: "installed ubuntu8.04 and lost OS"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by bluesalt on 2008-09-26
1. Downloaded Ubuntu8.04live through Unetbootin because I don't have a CDROM. Didn't intend to keep WinXP
Downloaded files and at the end of process rebooted.

2 WindowsXP and Ubuntu booted up.
Selected Ubuntu. Double clicked the install icon

3 Graphical installer came up; went through the steps until partitioning.
Choose not to partition since I wanted to use all of the disk space
Error message: The ext3 file system creation in partition #1of SCSI1(0,0,0) (sda) failed.

4 Hit Back button and went the steps in partitioning. same error message. 

5 Cancelled the process and exited from Ubuntu.

6 Restarted the notebook but error in loading Operating System.

Now that I don't have an OS, how can I install Ubuntu as my new OS. How do I use one of those generic external disk drives to boot up the note book again? Which Ubuntu file do I download? Is it possible not to go through the partitioning exercise on the HDD of my notebook and the external disk drive? I don't think I understand any of the GRUB stuff or having to get into DOS mode etc

Please help. Thank you.

---

### Post by Orange_and_Green on 2008-09-26
Hello bluesalt,

just immediately after bootup, you can go into the Boot Sequence Menu / BIOS setup and see if it gives you an option to boot from an external USB CD drive. To enter BIOS setup, you have to press a key (or key combination) immediately after switching on the computer. It's usually F10, del, esc, F2, but that varies from manufacturer to manufacturer, you can read which one applies to your system on the very first screen.

Or, you could consider making a bootable Ubuntu installation USB stick, either with Unetbootin or manually as described here (bottom half section of the page):

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I hope this helps. Good luck:KS

---

### Post by bluesalt on 2008-09-26
Hi Orange&Green 

I will try this. Thanks for the directions. I want to be able to say Ubuntu is SIMPLE-ly fantastic, too.

Cheers

---

### Post by bluesalt on 2008-10-01
Hello

I downloaded onto the USB stick using Unetbootin. I have a IBM T30 that's about 5 years old which doesn't hv a USD2.0 port, I guess. Nonetheless, I went to the Bios menu to reboot through "removable devices". Nothing happened, same error message: error in loading Operating System

Will appreciate help in this.

---

### Post by seshomaru samma on 2008-10-01
can your computer boot from network?
another option will be to physically take out the hard disc, install ubuntu using another computer and put it back in.

---

### Post by bluesalt on 2008-10-01
Thanks. 
But not able to boot from network. 
I would like to know how the 2nd option works. How do I connect the hard drive to another computer? I'm a real beginner.

---

### Post by bluesalt on 2008-10-01
I found a possible problem with the downloading of files into the USBstick. I had downloaded from Unetbootin using windows version. It seems that there were some files which Vista would not download. Does this happen?

---

### Post by seancarlgrech on 2008-10-01
> How do I connect the hard drive to another computer?
 
all you have to do is:
 
back up all your usefull data
turn of your computer
open your pc case and unscrew and unplug the drive
then connect it to the other computer and try installing ubuntu :D
 
 
if possible get some friend or someone who is more qualified to do this work for you...

---

### Post by nowshining on 2008-10-01
what speed did u burn the cd/dvd??

it's suggested to burn at 4x or slower and to check the mdchecksum of now burnt disc and see if it matches up with that of the one shown on the ubuntu, etc.. download pages, etc..

---

