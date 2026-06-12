---
title: "Installing ubuntu 11.10 on an external hard drive"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by markhamdude on 2011-11-13
[COLOR=Black]Just wondering how [/COLOR]I could install ubuntu 11.10 onto an external hard drive. I am currently running windows 7 and am a complete newbie :confused:

---

### Post by nosmadar on 2011-11-13
This may or may not work. But there's a procedure for creating a bootable instance of Ubuntu on a USB jump drive.  Maybe that would work for your situation. Only thing is I don't know if you need a working Ubuntu installation to build it in the first place.

---

### Post by beew on 2011-11-13
Create a live CD or live usb*. Boot into it, then attach your external drive and click install Ubuntu, when the screen comes up asking you how you want to install, choose "something else". Then locate the external drive you want to install Ubuntu into from the partition chart to see the layout (it will be sdb or sdc. sda is your internal hard drive, don't touch it! If you boot from a live CD, the external drive would be sdb, if you boot from a live usb, it will be sdc, but just to be sure read the partition table carefully) 

You can then decide how big a partition(s) you want to make for your Ubuntu install. There should be at least one partition, formated as ext4 and set mount point to "/" (from drop down) I would use two partitions however. One "/" partition for the system and a "/home" partition for data and settings. 20G for "/" should be more than enough (typically you will use  < 15G) . The /home partition can be made as big as you like because it also stores data (also formatted as ext4) 

Finally you need a swap partition (Linux swap) and usually it is about 1.5 times of ram.

**Then comes the really important part.** In the bottom of the same screen there is a box to choose where to install the bootloader. Make sure you choose the target external drive (sdb or sdc in our case) The default is sda, if you don't change the default you wouldn't be able to boot into windows without the external drive being attached!

Then just keep pressing next (or forwared) to complete the installation. 

After that you can attach the external drive in any machine and boot into Ubuntu (not just the one that creates the installation) provided the hardware supports it. However, the system would not be portable if you install proprietary graphic driver, because then it will be able to work only on machines that use the same graphic driver.  If your computer has a Nvidia card (I think ATI as well but I am not sure) the proprietary driver will be installed if you check the box to install third party software during installation.

P.S. Some people recommend that you remove the internal drive before the operation, I see no need of that and never do it. As long as you make sure to install into the correct drive and install the bootloader accordingly there is no need to take that extra step.

* I would recommend a live usb over a live CD as it is faster and it is easier to make, you  don't need any special burning tool or a CD ROM, and you don't need to set any burn settings. To create a live usb in Winodws use either unetbootin or LILI [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

**EDITED:** Make sure you are connected to the ineternet when doing all these!

---

### Post by beew on 2011-11-13
> **nosmadar said:**
> This may or may not work. But there's a procedure for creating a bootable instance of Ubuntu on a USB jump drive.  Maybe that would work for your situation. Only thing is I don't know if you need a working Ubuntu installation to build it in the first place.

I think you are talking about a live usb with persistence, that is not the same thing. Apart from the size limit (no matter how big your flash drive is it is limited to 4 G because of the limitation of FAT file system) it is very slow and doesn't support system level updates (such as kernel update) or installing proprietary graphic card if desired.  You can make a full install into a flash drive (ext4) with the same procedure as I described in my last post, but it will still be slow. A full installation into an external hard drive is much faster than installing into a flash drive even with the same size.

Installation into an external harddrive is a *real* install with the proper file system and supports all operations that you can perform with an internal installations, it gives you the full performance and it is fast (boot up time may be somewhat slower than an internal install depending on the BIOS)

BTW, installing in an external drive definitely works. I have a few *buntus and other Linux distros in a multiboot external drive which I use as a portable and to test new releases. For example, I have 11.10 installed there for testing, at this stage it is still too buggy for me to even consider installing it in my work machine (which runs 10.10, and I will replace it with 11.04 in a few weeks,--which I have tested to my satisfaction on the external drive)

---

### Post by oldfred on 2011-11-13
I have installed to an 16GB external flash drive just like beew described, except I usually format in advance and then use manual install (Something Else). But nowadays you do not have to format in advance.

If you would like some screen shots showing the same thing:

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

