---
title: "GRUB error"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by cheatos on 2012-02-20
Hi,

I wanted to install lubuntu on an external HDD with my laptop, but I accidently installed the bootloader on the HDD of my laptop, now when I boot I always get a command line with
```
error: no such device: xxxx
grub rescue>
``` where xxx is the UUID? of the HDD I used to install, its a pretty long number and I don't think this is very important, so I don't wrtie it all down here..

However, when I insert the HDD it boots to the normal GRUB screen and I also can boot into Windows which I have on the laptop.
I already tried a search for a GRUB folder in Windows and lubuntu, but I couldn't find anything...

Also the help command doesn't get me anywhere, as it says Unknown command 'help'

Any help would be greatly appreciated!

---

### Post by wolfen69 on 2012-02-20
You will need to reinstall GRUB. [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by cheatos on 2012-02-20
But I don't need GRUB on my laptop, as Windows is the only OS on this laptop, isn't there a solution of removing grub completly?

EDIT:
Either way I tried this to make my laptop bootable again, but with no effect. When I try booting without the LiveUSB inserted it still goes to the grub-rescue screen.

I have used the boot-repair toll from the GRUB wikipage. Maybe I hve done something wrong, could you please help me further?

---

### Post by cheatos on 2012-02-21
Bump

Can someone please help me? I dont want to have a laptop which can only boot with a usb-stick inserted.

---

### Post by oldfred on 2012-02-21
You want the Windows boot loader on the internal drive & grub on the external drive. In BIOS you set external as first & internal as second. If external is found it boots with grub and gives you a choice of Windows or Ubuntu. If external is not found BIOS uses internal and directly boots Windows.

Walk thru including fixing grub's reinstall which would be back onto the internal drive on updates.

Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Or you can manually reinstall, grub, Windows boot loader and fix the locations where grub reinstalls on updates:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From Ubuntu run this first and install grub to sdb or whatever device the external drive is:
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Then install the Windows boot loader to sda or use a Windows like boot loader that you can install from Ubuntu.

---

### Post by cheatos on 2012-02-22
Thank you oldfred, this is a lot of input, I'll be working my way through as I didn't understand everything at the moment ;)

---

### Post by cheatos on 2012-02-23
Thank you oldfred, I have tried the second link today and my laptop booted without a problem!
Thank you very much for that easy tutorial.

I'll mark this as solved now.

---

