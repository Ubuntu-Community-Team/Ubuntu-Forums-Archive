---
title: "Where can I find syslinux.cfg in ubuntu 10.04.4 x64?"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by cedricwaltercson on 2012-02-26
Hi,

So I keep getting this message on startup before the ubuntu splashscreen loads:

**_"pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000ce9ff]"_**

[FONT=Arial]And I've been searching on google to fix this and i found out that this has to do with the bios and that there is a quick fix...
In order to "fix" this I need to add "**pci=nocrs"** on syslinux.cfg.

But unfortunately i don't know where syslinux.cfg is...:confused:
Can anyone tell me where I could find syslinx.cfg?

note:I got this message after updating the linux kernel to 3.0 :(
     I had to update to 3.0 as it includes a patch for elantech touchpad.[/FONT]

---

### Post by Karlchen on 2012-02-26
Hello, cedricwaltercson.

I would be amazed if Lucid Lynx 64-bit had returned to using syslinux.cfg, because Lucid Lynx 32-bit uses grub.cfg for such settings. :wink:
To be a bit more precise, syslinux.cfg is not used by the grub2 bootloader which Lucid Lynx uses.
Grub2 can be re-configured by
+ editing the file /etc/defaults/grub
+ running the command **sudo update-grub** afterwards.

As it seems to be impossible to boot kernel 3.0 on your system to the state where you can edit /etc/default/grub and update-grub, you might boot your previous kernel and do so.
In case there is no previous kernel which can be booted, you might use a live system (CD / DVD / USB stick) and edit /boot/grub/grub.cfg on the harddisk(!), not on the live boot device, directly. 

HTH,
Karl

---

