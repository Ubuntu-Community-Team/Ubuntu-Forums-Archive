---
title: "Totally new to Ubuntu/Linux, having a problem with booting."
date: 2018-01-08
forum: New to Ubuntu
---

### Post by albatrozz on 2018-01-08
Hi all, 

I'm a brand new Linux user and still learning the very basics.

I decided to give myself a project and turn an old Windows PC that was sitting around into a Linux machine just to see what it does/can do.

I performed a totally clean install with the help of parted magic, as it wasn't a computer in use. 

After first installing Install, I was be able to log in but the system would freeze right after login. A little digging on the net suggested this was a graphical issue, right enough I was able to enter the via recovery mode and change drivers about (it was set to X.org server - Nouveau). 

Now the issue is whenever I boot, following the initial boot screen I' left with a blank screen and nothing. 

I am able to enter Ubuntu through recovery mode and it appears, as I believe the full experience should base don videos of Ubuntu I've been watching. 

The machine has a Nvidia GTX 555 and Ive changed the driver to all of the available Nvidia ones and the same problem occurs each time. Any thoughts on what might help.

P.S.


Drivers I have tried =

Nvida binary driver - version 3.84.90 ; 
Legacy Binary - v. 304.135
Binary - v.340.102

Running Ubuntu 16.04


All the best

---

### Post by oldfred on 2018-01-08
You should only install the correct version for your card. If newer video card, you can install the newest driver using the ppa.
But if you did not totally purge before installing another driver, you get conflicts as new install does not erase old install of driver.

       Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

It looks like you can use newer drivers. But the very newest driver primarily has updates to support the newest nVidia cards/chips. Eventually the freeze a version for the older cards.

 #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
ubuntu-drivers devices 
    
 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by albatrozz on 2018-01-08
Thanks for the advice,

I tried all of what you suggested, unfortunately, I face the same error, upon reboot, after boot screen a brief purple screen, then blank.

---

### Post by Autodave on 2018-01-08
Can you give us the specs of that machine?  That may help figure out what is happening.

---

### Post by mastablasta on 2018-01-09
> **albatrozz said:**
> 
I tried all of what you suggested, unfortunately, I face the same error, upon reboot, after boot screen a brief purple screen, then blank.

are you sure the screen is not on another output ? try moving the cables at the back on the nvidia GPU. no matter what i do the screen is always thrown to dvi output first and only later switches to VGA (after i set it as default in the OS). this kind of thing is really annoying. i mean the card can't recognise which monitor is on it.

---

### Post by albatrozz on 2018-01-09
So the system im running on has the following specs

Processor = i5 - 2320 - 3.00 GHZ
GPU = Nvidia Geforce GTX 555
RAM = 8GB
1TB Harddrive
64bit system

(@ mastablasta - The GPU has two DVI ports, tried them both with no luck, its got what I presume is a micro HDMI also, but I have no cable fore this. as i say Ubuntu seems to be fully graphically available through recovery mode, just not on a normal boot)

---

### Post by Autodave on 2018-01-09
You may want to try removing the Nvidia card and using the built in graphics.  At least you may get a working machine.

---

### Post by oldfred on 2018-01-09
Recovery mode uses nomodeset.

You often have to boot with nomodeset, until you install proprietary driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by albatrozz on 2018-01-09
Unfortunately this doesnt work either, It doesnt get past the screen where it says the ram is starting

---

### Post by oldfred on 2018-01-09
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by albatrozz on 2018-01-10
I tried the Boot-Repair, still the same issue, but her is the summary

[http://paste.ubuntu.com/26363319](http://paste.ubuntu.com/26363319)

Hope this helps

---

### Post by oldfred on 2018-01-11
You installed in UEFI boot mode, with LVM & full drive encryption.
I do not know LVM, other than it is an advanced volume management system for volumes inside standard partitions.
And any maintenance you do, you must make sure you have unencrypted your / (root).

Report also says Secure Boot may be on. Make sure it is off.

My opinion is the LVM is a pretty advanced. Knowledgeable users especially those with servers seem to like it. And it is the only way to get full drive encryption.
If you do not need the encryption, better to use a standard install. If you have to have full drive encryption, you have jumped into the deep end of the pool, and sink or swim. Or you have much to learn.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager)
[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

### Post by albatrozz on 2018-01-11
Ah I see, I wasnt sure about the encryption side,

So you think reinstalling ubuntu all together without the encryption may help the issue?

---

### Post by Geoffrey_Arndt on 2018-01-11
Yes - - a simpler install completely avoids LVM and encryption.  I wish the Ubuntu installer would nest LVM & encryption under an "advanced" tab or expandable caret.   But, because systems using Nvidia or ATI run best with those closed drivers, it is common to use the "nomodeset" boot option.   Read up about it or watch some media on youtube [https://www.youtube.com/results?search_query=nomodeset+ubuntu+16.04](https://www.youtube.com/results?search_query=nomodeset+ubuntu+16.04)

BTW - - if you have any older (non uefi) PC's with Intel graphics, Intel Wireless . . . the install process is so easy "even a Caveman could do it."

---

