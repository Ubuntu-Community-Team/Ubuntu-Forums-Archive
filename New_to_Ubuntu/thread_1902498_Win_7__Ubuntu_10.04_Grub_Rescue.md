---
title: "Win 7 / Ubuntu 10.04 Grub Rescue"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by D4J0K3R on 2011-12-30
Hi,

I have a dual boot computer.
4 Hard drives.
Hard drive "A" has windows 7 Ultimate 64 bits on it.
Hard Drive "B" has Ubuntu 10.04.3 LTS on it.
95% of the time I use Ubuntu, but once in a while I go to Win7.
When I restart my computer to go back to Ubuntu, I'm greeted with a "grub>rescue" message.
This happens quite frequently I must say.
Is there a way to prevent that?
I'm tired of re-installing Ubuntu every 2 months...
I know I can pop in the Live CD to re-install Grub, but it is beyond my knowledge & I couldn't find a tutorial that could help me.
Why Grub keeps deleting itself every time I go in Windows?

Thank you!

---

### Post by TeoBigusGeekus on 2012-01-01
Why don't you try running a virtual machine in ubuntu, instead of dual booting?

---

### Post by drs305 on 2012-01-01
> **D4J0K3R said:**
> 
Why Grub keeps deleting itself every time I go in Windows?

Thank you!

Most likely part of the MBR is being overwritten by Windows apps such as DataSafe, HP ProtectTools, Dell Recovery, Adobe Flexnet, and some others. Every time you boot one of these apps writes to an extended part of the MBR which is also used by Grub. Thus, once you boot Windows, when you try to reboot Grub part of its information is missing.

You may have to uninstall DataSafe (or the others mentioned) to prevent it from overwriting Grub.

Here is more information:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR")

---

### Post by I_can_see_the_light on 2012-01-03
You could try [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Ubuntu"). It creates an entry in the windows bootloader to chainload into GRUB. I use it myself and haven't had any problems so far.

> Due to a bug in Ubuntu 10.04+, the current steps are rather more convoluted than they used to be in previous versions, requiring the user to first give control of the MBR to GRUB2, and then use EasyBCD to put the Windows bootloader back in control. We have brought this issue to the attention of the Ubuntu developers, and hope to have it resolved soon.
I wouldn't worry about this since you are already using GRUB as your bootloader.

---

### Post by jvcastle on 2012-01-03
I've got the exact same problem dual booting on a Dell Precision 750
It came with win7 on the first drive, I made the rest ext4 for Linux.

As best I can tell every new install of the kernel kills the win7 boot, and I have to run "fixboot" from the win7 disk to take care of that.  Every now and then Windows does something to the Linux boot and I have to repair that too.  Oddly, this seem to start when grub2 appeared.

This is the only machine of 4 I have this problem with -perhaps it is some sort of Dell App running in win7 as suggested, but haven't been able to find a solution other than to keep win7 and ubuntu install disks handy...

---

### Post by oldfred on 2012-01-03
If you have multple drives, just install grub2's boot loader to the second drive and leave the Windows boot loader on the Windows drive. Then there is no conflict.

If you only have one drive, make a emergency boot USB or CD. For a flash drive just install grub to the flash drive and copy your grub.cfg to the grub directory and you have another way to boot.

To install to sdb:
sudo grub-install /dev/sdb

But grub may have set its memory to reinstall to sda, so use this also:
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

Shows how to create & edit grub.cfg, just copy in a boot stanza from your normal install & it will also boot it.
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

### Post by D4J0K3R on 2012-01-05
Thank you very much for all your answers!
But I sort of given up on the dual boot thing...
I have my desktop with win7 offline all the time & my netbook with Lubuntu for my online activities.

Thanks!

---

