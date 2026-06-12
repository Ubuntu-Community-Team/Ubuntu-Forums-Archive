---
title: "How to remove another Linux OS and get to GRUB"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by jaydoc on 2008-05-27
Hi...

I recently installed a KDE distro - PCLinuxOS Minime.... 

A great distro - but I have had it with KDE, at least for now....

GNOME on PCLinuxOS 2008 GNOME Remaster (on my Laptop), as well as on Ubuntu Hardy (Desktop) is at least as configurable as KDE, at the very least it suits me better.... Also there is still some problem with the infamous PATA Jmicron controller for Minime.

For these reasons I want to remove MiniMe from the Dual boot, and hand my desktop entirely over to Hardy....

The problem is - GRUB has PCLinuxOS as default boot. How can I format that partition, yet still retain the GRUB menu...? MiniMe detected Hardy Install during installation and offered to add it to the menu for me....

So how do I remove MiniMe and retain Ubuntu...?

Thanks.:)

---

### Post by Paqman on 2008-05-27
First thing to do is sort Grub out. Grub comes in two parts as far as you're concerned:

The MBR
The file /boot/grub/menu.lst

Every copy of Linux you've installed will include it's own menu.lst file. Basically, the Grub setup on the MBR points to one of them. This would normally be the last one you installed.

So you want to make sure Grub is pointing to an installation that isn't going to be wiped. To do this:
```

sudo grub
root hd(0,0)
setup (hd0)
quit

```

You'll need to change the hd(0,0) to match the location of the copy of menu.lst you want to use. Grub numbers from zero, so hd(0,0) is actually drive 1 partition 1 (probably called sda1 elsewhere in your system)

You can also remove any entries to the distro you're wiping from menu.lst.

Once Grub is quite happily booting you using a menu.lst contained on a partiton you're keeping, you can fire up Gparted and format/delete the partition containing whatever distros you want gone. And that's it!

---

### Post by Duck2006 on 2008-05-27
Some reading on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by jaydoc on 2008-05-28
RED ALERT..... SOS..... SOS.....!

@paqman

I did exactly as suggested..... And it was all well.... I got back my Ubuntu Grub Menu intact as it was....

So I went in and deleted the partition that had MiniMe on it.... I was meaning to format it later.... so didn't format it. it was left empty....

Maybe it led to the numbering of the partitions going wrong, but on reboot there was just a black screen with a message - no boot partition found. 

The greatest problem is the installation Hardy CD seems to have gone corrupt, so I have to use another distro's liveCD ( PCLinuxOS 2007) to boot.... and I saw that my Ubuntu partition has the data safely. that's a relief.

SO HOW CAN I GET BACK MY INSTALL. What went wrong....?

Do help out.

---

### Post by jaydoc on 2008-05-28
I did try the following to try and reinstall GRUB.

sudo grub
find /boot/grub/stage1
root (hd0,5)  **That was what I got from find**
setup (hd0) **everything seemed OK from the output I got....**
quit

Rebooted... STILL the SAME Problem.

---

### Post by meierfra. on 2008-05-28
Some bios  refuse to boot if you do not have a boot flag on a primary partition.  Boot from a LiveCD and type

```
sudo cfdisk /dev/sda
```
(You might have  to  change the "sda")

the "boot" tap on the bottom is for setting boot flags.

---

### Post by jaydoc on 2008-05-28
@meierfra  

I tried.... it doesn't work.....

Any other suggestion...?

---

### Post by meierfra. on 2008-05-28
I didn't had much hope, but thought it's worth a try. Just to make sure, you put the boot flag on a primary partition (sda1 to sda4)?

---

### Post by meierfra. on 2008-05-28
> no boot partition found.

Do you know whether this message was from "grub" or from your bios? (Sounds more like a message from you bios)

---

### Post by damis648 on 2008-05-28
i have a dell XPS M1530 and i got "no boot partition found" and i know it was from my Bios, so i am passing that to you, as it is probably your Bios.

---

### Post by bill0102 on 2008-07-04
What's Up all,  want to beat any game you play? check out this  [Top Cheat Codes Site]('http://vncheatcodes.com')
You can play and cheat any game you want from [PSP Cheat Codes]('http://vncheatcodes.com') to [Xbox Cheat Codes]('http://vncheatcodes.com') and many other [Game Cheat Codes]('http://vncheatcodes.com')

---

