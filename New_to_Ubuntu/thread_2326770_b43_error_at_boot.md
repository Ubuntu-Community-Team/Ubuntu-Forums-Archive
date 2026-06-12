---
title: "b43 error at boot"
date: 2016-06-04
forum: New to Ubuntu
---

### Post by tbruneti on 2016-06-04
Well not a great start!

I have an old Compaq C500 laptop and I though "After all these years I will give Linux a try".
So I read about UBUNTU and then found LUBUNTO and downloaded the latest ISO as the laptop only has 1Gb of memory.
I found out how to create a boot USB stick, on my Windows PC, and created one using the downloaded ISO.
SO FAR SO GOOD.

Changed the BIOS on the laptop and booted from the USB - English and Try without installing (I have Windows on the hard disk).
It began doing something and then
[B]b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/b43#devicefirmware]("http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware") and download the correct firmware for this driver version. Please carefully read all instructions on this website.[/B]

I tried that link and - WHAT??????? Human says NO!
So I searched the web and found LOADS of things none of which make much sense and most of which assume that you have a working LINUX system and give loads of different commands to try. **I can't even boot?**

I tried disabling the WiFi in BIOS and get the same errors as above.
I tried adding **b43.blacklist=yes** by pressing F6 and ESC, then enter that at the end of the line (but before the ---).
In fact I tried adding that just about all over the line.
When I press ENTER it gets the same error as above.

I must admit that I am totally bemused as I have the laptop plugged in via LAN and I thought it would boot using THAT and then automatically download any WiFi drivers it  needed. Or at least that was what I would have expected. At very least boot without WiFi.

[B]Surely there must be a _SIMPLE _way to manually add these drivers to the USB pen?
Or a simple set of instructions to get me working in Linux?[/B]

NOW I REMEMBER WHY I NEVER GOT INTO LINUX.
[B][SIZE=5]
HELP ... PLEASE  [/SIZE][/B]

Sad Tony

---

### Post by grahammechanical on 2016-06-04
Please do not shout.

The developers of Ubuntu/Lubuntu believe in Free and Open Source Software (FOSS). For this reason the Ubuntu/Lubuntu ISO image does not contain proprietary video or wireless drivers.

The developers also like to make things as easy as possible. And so we can install some proprietary drivers during installation by ticking the box "Install third party software." We can also install proprietary drivers after installation. We use the Additional Drivers utility.

All of that assumes that we are connected to the internet by a wired (ethernet) connection. If that is not possible and we must use WiFi to install Linux we need to do one of two things: (a) set up a WiFi connection during the installation process. (b) we run the live session and set up a WiFI connection. 

That assumes that the Linux kernel has a kernel module for our WiFi adapter. If we need a proprietary WiFi driver then we have little alternative to setting up a wired connection.

---

### Post by RobGoss on 2016-06-04
With out providing any information about your system like **specs** will only make it harder to determine why your system won't boot

You can start out by telling us what version of Ubuntu you have installed on this machine if it is a older computer you might want to try a **lighter** distribution like [Lubuntu]("http://lubuntu.net/") or [Kubuntu]("http://kubuntu.org/") they require less to run and may be what your looking for

When getting started with Linux you can be sure it's a learning curve but at the end it's all worth it. These forums have all the answer's you need it's just a matter of time before your problem is solved

---

### Post by tbruneti on 2016-06-05
Thanks grahammechanical

Why are people so upset y CAPITALS (CAPITALS not SHOUTING).
Thanks for the explanation - but as I have explained IT DOES  .. sorry, it does not boot up with Ethernet (which was what I expected).
I can certainly understand that the developers (is that the we?) cannot add every driver in the world.

Any idea how I can "we can install some proprietary drivers during installation by ticking  the box "Install third party software." We can also install proprietary  drivers after installation. We use the Additional Drivers utility.". I do not recall seeing a box anywhere?

I just want to add the WiFi drivers to the USB stick - but how?

---

### Post by tbruneti on 2016-06-05
Hi RobGoss 

I thought I had already posted that I have a Compaq c500 and that I was trying to install the latest LUBUNTU.
Downloaded yesterday from [http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/lubuntu-16.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/lubuntu-16.04-desktop-i386.iso)
It hardly matters as it seems that the b43 problem is there for UBUNTU and LUBUNTU since V12.

I'm not sure exactly what WiFi card I have (have not got as far as finding the driver yet) - I think its a Broadcom 4311.

As I said before I just want some idea how to add the WiFi drivers to the USB drive.
Or failing that how to bypass the error so that LUBUNTU actually runs and I can then use the built in Ethernet card and a cable.
Surely I cannot be the only person in the world with the b43 problem?

Thanks for the "hope" and this seems like such a trivial issue that I cannot understand why I cannot find a solution myself.
You should have heard all the swearing yesterday, and no matter how much I shouted at my laptop it still would not boot LUBUNTU.
I am fairly familiar with Windows but have not used UNIX for about 20 years (it was a little bit bigger than my laptop ... and no WiFi).
Hopefully I can get my old laptop working with LUBUNTU (or ANY other version of Linux) and get some experience of Linux.

---

### Post by jeremy31 on 2016-06-05
I would see if Ubuntu 12.04 will boot on the Compaq.  I have never seen that error cause a boot issue.  Once Ubuntu is installed with an ethernet connection you just ```
sudo apt-get update && sudo apt-get install firmware-b43-installer
```
Reboot and wifi works

Boradcom's licensing prevents any Linux distro from including the firmware in the ISO

---

### Post by wildmanne39 on 2016-06-05
This was a common bug a few years ago with 12.04.
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/956677](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/956677)
You said you tried to add ```
 b43.blacklist=yes
``` but I think you added it to the wrong place.
It is added to the grub at boot up once you enter the grub menu you have to press e I believe to edit the line that needs edited.

I have to leave soon I am traveling back home today but I am sure jeremy31 can walk you through the process if you need more help.
Thanks

---

### Post by jeremy31 on 2016-06-05
Tony, is this Ubuntu 16.04?  It sounds like you have placed the command in the correct place but I am sure that command doesn't work as it did

Try ```
modprobe.blacklist=b43
```
EDIT: that doesn't seem to work either

I think I would try booting the ISO after removing the wifi card.  Some laptops you only have to remove a couple screws to get to it.  Looks like maybe 3 for yours.  One to remove the cover on the bottom below the touchpad and 2 screws securing the wifi card to the motherboard

---

### Post by tbruneti on 2016-06-05
Hi jeremy31
Yes it is 16.04, from the link above, and I have left it for a while it just stays on the screen with the three b43 error lines in my original post.
I'm afraid I have no idea how to add this to the GRUB?
I pressed the ENGLISH option then F6 and ESC. A line was on the screen that I could edit and I typed (SPACE)**b43.blacklist=yes**(SPACE) before the --- at the end.
I also tried the same command after the --- and in between every other, what seems like, commands on that line.
None of them did any good.

I will try your modprobe.blacklist=b43 in the same place.
Even though you say it did not work for you - worth a try?

I will get back as soon as I've done that.

THANKS

---

### Post by tbruneti on 2016-06-05
Well....

I tried that **modprobe.blacklist=b43** and it worked, sort off.
The b43 errors did not appear this time, but a little cursor flashes on the top left and ........... NOTHING.
Just a black screen and the little cursor flashing, I left it for an hour.

So I downloaded LUBUNTU 15.10 and burnt that to my USB and it boots up no problem.
Well it boots but I have no WiFi.

Where and how do I run that **sudo apt-get update && sudo apt-get install firmware-b43-installer**
Please note that I am not installing this to my hard disk drive (I have Windows on it) so booting from the USB pen drive.

Can I save changes to the USB drive so that it becomes a portable LUBUNTU with MY settings and drivers (and documents?).
Obviously if I like LUBUNTU I will try dual booting it (somehow?) or I may get another disk dive.
But for now I would just like to play with it from the USB stick

---

### Post by jeremy31 on 2016-06-05
I have never done a persistent pen drive install which is what you would need if you want to save to it.

The command is to be run in terminal, CTRL + ALT + t will bring a terminal window up in Ubuntu, it may work in Lubuntu also

After installing the firmware, you can try ```
sudo modprobe -r ssb
sudo modprobe -r b43
sudo modprobe b43
```
Hopefully it works but sometimes it will hang up in terminal

---

### Post by tbruneti on 2016-06-06
Thanks for your help Jeremy31.
I will play with LUBUNTU / UBUNTU and see if I like it, then decide if I actually want to install it.
I can't be bothered with installing the WiFi each time I boot, so I will just use the Ethernet cable - I'm quite happy with that.
The real problem was that LUBUNTU 16.04 locked up AFTER showing the b43 error.
I don't think it was the b43 error caused the lock up, but something to do with the latest ISO and my PC.
I will just use the previous version which seems to work.

I have also seen some instructions for creating a "persistent pen drive", which is what I think I want, so I will try that latter.

Thanks for your help.

---

