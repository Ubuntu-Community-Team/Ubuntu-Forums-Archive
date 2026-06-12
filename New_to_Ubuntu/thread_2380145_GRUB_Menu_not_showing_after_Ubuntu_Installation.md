---
title: "GRUB Menu not showing after Ubuntu Installation"
date: 2017-12-13
forum: New to Ubuntu
---

### Post by fpribeiro2 on 2017-12-13
Help!! I've been stuck in this situation over a month now don't know what to do... I tried everything.
I'm trying to Dual Boot Windows 10 and Ubuntu 16.04.3 LTS and i succeeded in the installation but when i restarted the PC It simply goes straight to Windows. The PC is an Acer Aspire E5-573G,
BIOS is InsydeH20 with UEFI and Legacy modes. I installed everything on UEFI Mode with Secure Boot disabled. Things I've tried:
[LIST]
[*]BootRepair (Recommended) within a Live Ubuntu from the PEN DRIVE I used for the installation.
[*][http://deshack.net/ubuntu-dual-boot-grub-doesnt-start/](http://deshack.net/ubuntu-dual-boot-grub-doesnt-start/) <----- This tutorial although some steps didn't work like  "grep -v rootfs /proc/mounts > /etc/mtab" gives an error about it being input and output...
[/LIST]

The report from bootrepair shows something  like 
 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
The paste is this link: [http://paste.ubuntu.com/26179043/](http://paste.ubuntu.com/26179043/)

Any help would be appreciated! Thanks in advance

---

### Post by westie457 on 2017-12-13
Welcome to the Forums [[COLOR=#000000]fpribeiro2[/COLOR]]("https://ubuntuforums.org/member.php?u=2085208")

First boot into Windows then go through the following steps in order.


[LIST]
[*]Type Control Panel in the search box.
[*]Click Control Panel.
[*]Click Power Options.
[*]Click Choose what the power buttons do.
[*]Click Change settings that are currently unavailable.
[*]Scroll down to Shutdown settings and uncheck Turn on fast startup.
[*]Click Save changes.
[/LIST]

Then you can do either of the 2 following things. Both involve entering the UEFI settings pages.

The first is to disable 'secure boot'.
The second (recommended) is to set a supervisor password to unlock some further settings to enable 'trust'. This easy to do and involves agreeing to some options.
When the settings have been changed you can clear the password if you wish.
Press F10 to save and exit the settings pages and reboot into the Grub menu.

Acer is so far the only manufacturer have this policy for the UEFI settings.

---

### Post by fpribeiro2 on 2017-12-13
I disabled fast startup like you said, still when I press F12 to see the available boot options it only shows the Windows Boot Manager and the Pen drive IF inserted... I think windows doesnt recognize grub but i don't really know that's why i'm here lol
Thanks for the help anyways

---

### Post by westie457 on 2017-12-13
Did you follow the part after disabling fast startup?

The second part of my reply can only be done by tapping on the F2 key at power on.
While you are in the Settings pages you should be able to arrange the boot order to have Ubuntu at the top of the list.

---

### Post by fpribeiro2 on 2017-12-13
Yeah Yeah I did that too, in fact it was already done... Except for the trust option can't seem to find that, but i have set the password and disabled secure boot

---

### Post by oldfred on 2017-12-13
Trust is a unique requirement with Acer.
Many with somewhat older Acer also need update to UEFI. Even older threads had users downgrading to an older UEFI/BIOS.

 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by fpribeiro2 on 2017-12-14
Thanks You so much :):smile::smile::smile::smile::smile: The first link fixed my problem. Turns out it was indeed a PC specific problem... Thanks again!

---

