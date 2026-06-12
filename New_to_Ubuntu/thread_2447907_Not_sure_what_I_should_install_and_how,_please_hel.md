---
title: "Not sure what I should install and how, please help?"
date: 2020-07-28
forum: New to Ubuntu
---

### Post by kgaset on 2020-07-28
I finally have a spare computer that I'm able to set up as a personal server, but I already have some questions that I'm finding getting the answers to difficult.


[LIST=1]
[*]Should I install Ubuntu desktop or Ubuntu server? My plan is to hopefully do primary access to the server through my main machine using the command cell. However, being able to have the GUI is important as well if I'm trying to access the computer directly.
[*]Is there a way to install it directly onto an SSD while I have it hooked up through an SSD/HDD reader? My web searches have turned up things like GRUB, but I'm still not sure whether or not I can just download an installer and install it to an SSD or if it would honestly be easier to just set the other computer up and do a typical install via a USB drive.
[*]I'm considering doing a RAID on my SSDs as I have three of them but I've never done it before, is there anything I should know about RAID and Ubuntu? Is this something I should do before or after the install?
[/LIST]


Thanks in advance.

SOLVED:

I've gotten pretty solid responses. I'll look into RAID on my own. Thank you for the help!

---

### Post by ActionParsnip on 2020-07-28
If you want a GUI install Ubuntu. If you are OK with command line then install Ubuntu Server.
That's the only difference

---

### Post by Autodave on 2020-07-28
You didn't say the specs on your spare machine, but using it as a server and with a GUI, I would probably be looking at a lighter desktop such as Xubuntu or Lubuntu.

---

### Post by grahammechanical on 2020-07-28
> Is there a way to install it directly onto an SSD while I have it hooked up through an SSD/HDD reader?

I very much doubt that. Put the SSD into the relevant machine and install Ubuntu on to the SSD as if it was a hard drive. Which is what it  is. The install process of whichever flavour of Ubuntu you chose will install the bootloader (Grub - Grand Unified Bootloader). And also all the necessary hardware drivers.

The server install of Ubuntu will not include most of the default applications that come with a desktop install of Ubuntu. The desktop install of Ubuntu will not include applications that are normally required on a server installation. You might find it easier to install a desktop on the server edition than removing many default applications that come with the desktop install and you do not want.

As this is a spare machine you can experiment to get experience and then start a fresh when things don't work out as you want. I know nothing about RAID installations other than what I can read from internet searches. Just as you can.

Regards.

---

### Post by pbear42 on 2020-07-28
> **kgaset said:**
> Is there a way to install it directly onto an SSD while I have it hooked up through an SSD/HDD reader? 
Certainly it is possible to install to a USB drive (I have several multi-boot USB hard drives), so I've always assumed it's possible to do what you're thinking of, i.e., install to the drive then insert it to a machine.  I've not done it, though.  Two things to know.  First, will be tricky (and may not work) if either machine needs special drivers.  Second, there's a bug in the installer which will bollix the boot loader of a UEFI machine when installing to USB drive (or a second internal drive).  Several workarounds for that, of which I prefer (per [askubuntu]("https://askubuntu.com/a/1056079")) unflagging the internal drive's EFI partition during the install, then reflagging when done.

---

