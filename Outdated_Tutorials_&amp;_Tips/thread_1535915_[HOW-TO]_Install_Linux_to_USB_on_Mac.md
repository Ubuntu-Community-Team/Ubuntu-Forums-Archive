---
title: "[HOW-TO] Install Linux to USB on Mac"
date: 2010-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by krisman101 on 2010-07-21
_**This is a tutorial on how to install linux to usb on a Mac**_

To do this, you will need:

 An ubuntu disc or ISO (I used 10.04),

 A Windows installation disc or windows already installed (I used windows 7 64 bit), 

 A linux installation disc for any distro (tested with linux mint).

An intel mac (note that this will not work on powerpc)

The OS X installation disc which came with your mac

A wired keyboard and mouse to get linux set up (you can use the bluetooth keyboard and magic mouse in linux)

_**Intro**_

What we’re going to do is install linux to an external disc, and then wubi to the bootcamp partition, which will find the external linux distro, and insert an entry into wubi’s grub menu, giving us a quad boot of OS X, Windows, Ubuntu (Wubi), and another linux distro.



_**Installing Windows**_

So what we’re going to do first of all is install windows using Boot Camp. You can skip this section if you have already got windows on your mac.

To do this, you go into utilities, then run Boot Camp Assistant, which will guide you through partitioning your internal drive for windows. It’s really simple, but if you get stuck, you can find a guide online which will help you. Just be sure to install the drivers from your OS X disc.

_**Installing Linux on the USB Drive**_

I used a generic USB Hard drive with the MBR partition table for this, but flash drives should also work. 

What you’ll need to do is make sure there’s nothing important on the drive, and partition it how you want. For example, I used a 10GB partition on a 320GB disc. You can leave this partition as free space, or format it, it doesn’t really matter.

Now, to boot from the linux disc, either hold down cmd at startup to get the regular bootcamp menu. Insert your linux disc, and it should show up as WINDOWS, with a CD icon. Select it, and go through the menus. Install linux to your usb disc, using it as the / mount point.

You’ll need to install the bootloader to the external drive, so make note of it’s mount point [for me it was /dev/sdb]. *_**MAKE SURE YOU DON’T INSTALL IT TO YOUR INTERNAL DRIVE(S).**_* I don’t think you even need to install a bootloader, but I did anyway.

Once that has finished installing, make sure that you can boot into OS X, and bootcamp.

_**Installing Wubi**_

I did this using vmware in OS X, but it was still my bootcamp partition.

Insert your ubuntu disc, or mount an ISO with poweriso or daemon tools.

On the disc, run setup.exe, which will give you 3 options. Choose the option to install within windows, and follow the wizard. When bootcamp restarts, choose ubuntu from the windows bootloader. Ubuntu will finalize the installation.
To boot form linux, hold down cmd, choose windows, then choose ubuntu from the windows bootloader, which will give you a grub style menu, where you can boot into ubuntu, and the linux distro on the usb.


**Notes**

This does work with the apple bluetooth keyboard, as far as I have tested.

Each mac is different, so you should google how to get them working (sound, wireless, graphics, etc.)

---

