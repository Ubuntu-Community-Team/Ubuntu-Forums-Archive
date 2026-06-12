---
title: "Unusual dual boot scenario: existing Hardy system, existing XP HD from other system"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by chromedome on 2008-05-05
The back story is rather long and convoluted, but the title summarizes the scenario.  I have a pokey-but-adequate system running Hardy.  I have a second hard drive which contains a full XP Pro system and several years' data, belonging to my fiancee.  Since putting that into her new notebook is not an option, we'd like to dual-boot her XP drive on my existing Hardy system.

What's the cleanest way to do this, without risking her data?

---

### Post by phr0ze on 2008-05-05
The easiest thing is to choose the boot drive every time from the bios or bios boot menu.

---

### Post by fahadsadah on 2008-05-05
phr0ze: Not really.
chromedome:
Please install her hard drive in your computer, and then on Linux, run the following command:
```
sudo grub-install /dev/sda1
```
You will be asked for a password.
Then, on reboot, you should be asked whether you want to boot the XP or Hardy.
If not, please post the output of ```
sudo fdisk -l
``` here.
Thank you

---

### Post by KillerSponge on 2008-05-05
One thing: The Windows installation will probably refuse to boot. Windows does not take kindly to suddenly being placed in another machine. I tried it a couple of times, it always resulted in a blue screen.

---

### Post by chromedome on 2008-05-05
> sudo grub-install /dev/sda1

> /dev/sda1: Not found or not a block device.


What now?

---

### Post by eriqjaffe on 2008-05-05
> **KillerSponge said:**
> One thing: The Windows installation will probably refuse to boot. Windows does not take kindly to suddenly being placed in another machine. I tried it a couple of times, it always resulted in a blue screen.You should be able to use Microsoft's SYSPREP utility to "re-wrap" the system prior to throwing it into a new PC...

[http://support.microsoft.com/default.aspx?scid=kb;en-us;302577](http://support.microsoft.com/default.aspx?scid=kb;en-us;302577)

Sysprep on the old hardware, shut down, move the hard drive to the new hardware, reboot into XP and it should re-detect hardware.

Note I said "should".  Try this at your own risk.

---

### Post by chromedome on 2008-05-05
Unfortunately, the drive is in my machine in Atlantic Canada and the old machine is in California.  As I said, a convoluted backstory.

---

### Post by chromedome on 2008-05-06
> **KillerSponge said:**
> One thing: The Windows installation will probably refuse to boot. Windows does not take kindly to suddenly being placed in another machine. I tried it a couple of times, it always resulted in a blue screen.

We have her XP Pro CD, so the system should be able to find what it needs on there.  In a worst-case scenario we can download necessary files and save them to the appropriate places, then reboot and try again (the value of having another OS up and running on a given machine).

It may be tedious, but it won't be difficult.

---

### Post by brettg on 2008-05-06
OK, ignore everything above this (except the stuff relating to Windows dislike for extreme hardware changes) 

Here is what you need to do.

I am assuming that;

1) your linux is running off the first hdd @ /dev/hda

2) The windows install used to be the first hdd on the original PC

Stick the windows hd in as a slave so it becomes /dev/hdb

It is up to you to confirm that these are the correct drive assignments. On newer sata or raid systems they may be actually be /dev/sda and /dev/sdb

Assuming they are right, you need to (as root) edit /boot/grub/menu.lst

and add a section at the end after *** END DEBIAN AUTOMAGIC KERNELS LIST

add 

title Micro$oft Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

The 'map' lines remap the drives so that windows thinks it is running off the first hdd. Without this nothing will work. 

If all goes well you should be able to reboot and chooes windows option in grub menu.

---

### Post by chromedome on 2008-05-06
You da man, Brettg!

I'd already had a fit of lucidity earlier and run fdisk -l to find out how my drives were labelled.  Your post gave me the missing piece of the puzzle, and now we can boot her XP drive.  We've got a few hardware-recognition quirks to work out (more than I had with Hardy, btw) but it's up and running.

Now I just need to figure out how to slow down GRUB so we have more than the current half-second or so to select the desired option...

---

### Post by brettg on 2008-05-07
Glad I was some help

To slow down grub, edit the same menu.list and change the value;

timeout = 

and comment out like so;

#hiddenmenu

---

