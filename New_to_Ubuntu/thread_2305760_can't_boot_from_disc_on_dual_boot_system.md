---
title: "can't boot from disc on dual boot system"
date: 2015-12-08
forum: New to Ubuntu
---

### Post by mystmaiden on 2015-12-08
I'm running Windows 8 (rarely used) and Ubuntu 12.04 on my desktop. I need to boot from the Ubuntu cd to fix a partition issue but I can't seem to get that done. I go into bios, choose the dvd drive as first in boot order and it simply won't do anything. It either restarts in Ubuntu or Windows. 

I could use some help - I'm particularly concerned because at this point if I had some kind of crash that needed a repair, I'd be out of luck.

thanks,
mystmaiden

---

### Post by sudodus on 2015-12-09
Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and also tell us if it is running in [BIOS mode or UEFI mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Test_if_running_in_UEFI_mode).

If the computer is running in UEFI mode, you need an amd64 version of Ubuntu. If the computer has a 32-bit processor, you need an i386 version of Ubuntu.

There might be problems with the CD/DVD drive, and in that case it is a good option to make a USB boot drive from your Ubuntu iso file or from the DVD disk.

See this link [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by yancek on 2015-12-09
You might check the connections on both ends for the DVD drive.  Simple solution although not likely to be the problem.

---

### Post by kolumcaj-silvi on 2015-12-09
An alternate solution can be to try booting it from a bootable USB device created with a fresh .iso file and Unetbootin

---

### Post by mystmaiden on 2015-12-09
Thanks all for the replies. Below is the system info

UEFI mode
HP (can't seem to find the model number)
AMD A4-5000 APU with Radeon(TM) HD Graphics × 4 
Graphics - Gallium 0.4 on AMD KABINI
AR9485 Wireless Network Adapter

It's here where I run into some confusion. When I set this up I was running 12.04 LTS, now 'Details' is showing  64 bit 14.04 LTS though I did not realize I had upgraded at any point. In the updater would checking 'Ubuntu base' have done that? Also, lshw is currently showing only one active core, would that change if I were running more processes?

I was able to play a dvd movie just now, so I think the dvd player is fine.

Thanks again,


'

---

### Post by sudodus on 2015-12-09
In UEFI mode, you need an amd64 version of Ubuntu. It should be OK to use 14.04.1 LTS

**ubuntu-14.04.1-desktop-amd64.iso**

And either burn it to a DVD disk (I recommend the tool ***k3b*** and the slowing possible burning speed), or make a USB boot drive

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mystmaiden on 2015-12-09
I can't install k3b. It gives me an untrusted packages message, clicking okay or repair doesn't work. It just closes the untrusted message. Correction - I got it to install via synaptic instead of the software center

---

### Post by sudodus on 2015-12-09
OK, then you can try to use whatever tool you have, for example Brasero (but I prefer k3b). 'Burn an iso image'! (Do *not* create a data DVD with a copy of the iso file!)

After burning you should see several files and directories, when you insert the disk into the DVD drive.

---

### Post by mystmaiden on 2015-12-09
I burned a new dvd. making sure to choose the 64 bit one and voila' its working now. I really appreciate the help and replies.

---

