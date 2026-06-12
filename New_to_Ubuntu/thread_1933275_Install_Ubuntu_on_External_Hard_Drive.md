---
title: "Install Ubuntu on External Hard Drive"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by brymerr921 on 2012-02-29
This is my first experience with anything Ubuntu and Linux.

I have a 60 gb external hard drive that is attached to my Windows 7 (Home Premium SP1 64 bit) via USB 2.0.

I would like to install Ubuntu to this external hard drive somehow so I can install programs in Ubuntu, save files and have them remain, etc.  I would like that hard drive to be bootable, so I can choose to run Win 7 or Ubuntu when I start up.  If possible, I would also like to be able to run Ubuntu off that hard drive inside a virtual machine so I can have programs open in Ubuntu and Windows 7 simultaneously.

A step-by-step of how to do this would be great... Thank you so much!

 - Bryan

---

### Post by clausrei on 2012-02-29
> 
A step-by-step of how to do this would be great... 
I would try to make it a bootable Ubuntu device first. But how would you be able run Windows 7 on it ? Impossible, Windows doen't have any bootable external devices version of its OS - and you would always have to install Windows first.
The only possibility is you could keep some of the NTFS Partition but this is about it.

---

### Post by enjoijesus94 on 2012-02-29
> **clausrei said:**
> I would try to make it a bookable Ubuntu first. But how would you be able run Windows on it ? Impossible, Windows doen't have any boot-able external devices version of the OS - and you would always have to install Windows first.
The only possibility is you could keep some of the NTFS Partition but this is about it - as far as I can see.

right right 
but if he installed windows first then he would have to back up his grub and install windows then install his linux partion.

other than that your right man.

---

### Post by ixtok on 2012-02-29
I have used external drives and usb sticks with ubuntu installed on them, used like a normal hard drive. When I want to boot the operating system on them I use my computers key sequence to not boot from my normal hard drive but to choose the external drive.

When I installed ubuntu on my external drive, I chose to have the boot loader also installed on that drive, the reason being that if you do not choose this option and you start your computer with out the external drive attached, the computer will not even boot your windows.

I suppose that when you install ubuntu on the external drive you could also create a partition which windows would recognize, I guess in that partition you could create the virtualbox hard drive, but I think that if you install virtual box in windows with ubuntu as a client then the ubuntu install would be wherever your windows program files is, normally on your normal hard drive.

---

### Post by brymerr921 on 2012-02-29
Thanks for all your help.  Unfortunately, I'm still stuck.  I downloaded Windows Virtual PC, and burned the ISO files for Ubuntu on a CD.  I open Virtual PC, click create new virtual machine, tell it to save all files on the external hard drive, allocate 2GB of ram, and double click on the new machine to open it.  It opens, displays the Ubuntu logo with the four dots going across the screen, and after it does that for a few minutes the window spontaneously closes...  What do I do to get it installed?

---

### Post by dave2001 on 2012-02-29
Hi Brymer,
Welcome to Ubuntu! As another former windows slave, I got to say, I love me some 'buntu. I still have to keep my win7 install around, mostly for work software. So I have tried a number of different things to have both OS's.

Personally I think the best thing is a dual-boot computer, with the internal HDD divided into partitions to easily accomplish this. Getting that done is a whole 'nother can o' worms though.

I digress, to answer your question. Installation on external HDD.

1. Insert Ubuntu CD into drive. 

2. Connect external HDD via usb.

3. Reboot computer (your computer will probably load ubuntu off of the Live CD, but if it does not, you'll need to enter your bios setup and change boot devices, or pick your CD-ROM drive as a temporary boot device).

4. Ubuntu loads up (the Live CD will run ubuntu in your RAM only).

5. Choose the "install ubuntu" icon on the desktop.

6. Follow the prompts and choose to install Ubuntu on your external HDD(not your internal Windows drive!).

CAUTION! Make absolutely sure you also choose to install the bootloader on the external HDD and not the drive with Windows on it. Ubuntu usually defaults to installing the bootloader on the first internal drive it finds. If you get this step wrong you'll have to repair your windows installation. (If your worried about this happening, simply disconnect your internal hard drive before step 3, and leave it disconnected for the duration of the install).

If everything goes well, you should have a fully functioning, Ubuntu installation on your external drive. There are ways to have ubuntu integrate and "play nice" with your windows drive as well, but that all comes later. As with any computer work, I'd recommend having a recent backup HDD image handy in case you screw up!

Good luck and let us know how it goes!

---

