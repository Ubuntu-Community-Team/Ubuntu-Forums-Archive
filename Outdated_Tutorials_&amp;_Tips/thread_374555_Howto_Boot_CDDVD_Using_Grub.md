---
title: "Howto: Boot CD/DVD Using Grub"
date: 2007-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Jose Catre-Vandis on 2007-03-02
To avoid using the bios option to set boot from CD/DVD, or to help get incalcitrant  bootable CDs or DVDs to boot, you can add Smart Boot Manager/MemDisk to your boot options in Grub and boot from Grub instead of using your bios.

You need a working grub loader installed.

First off, download these files attached:
[ATTACH]54347[/ATTACH]
and untar

then copy them to your boot directory:
```
 sudo cp memdisk sbm.bin /boot
```

then open up menu.lst in your editor (I have used nano here)
```
 sudo nano /boot/grub/menu.lst
```
and add this to the bootable options (not in the magic section)
```
title=SBM-Boot a CD
kernel /boot/memdisk
initrd /boot/sbm.bin
```

Next time you reboot into grub, you will see a new entry "SBM-Boot a CD"

With your CD/DVD in the drive, select this option, and you will get the Smart Boot Manager menu.
Scroll down to the CD-Rom option, press "Return", and then "Return" again out of the confirmation dialogs.

Your CD/DVD should now boot.

Tested on Ubuntu Edgy 6.10
Thanks to the Gentoo Wiki for guidance
Just retrace your steps to remove this option.

Enjoy

---

### Post by Skerit on 2007-12-23
Ahh, nuts, you can't get those files anymore ...

Got another link?

---

### Post by sheepdogj15 on 2009-01-03
hey cool. i'll give it a try

---

### Post by shadinata on 2009-06-09
thank you, it works :)

---

### Post by black plague on 2009-06-09
Very cool tip!  Now I'm curious to know if there's a way to do the same with bootable USBs........:D

---

### Post by Jose Catre-Vandis on 2009-06-11
> **black plague said:**
> Very cool tip!  Now I'm curious to know if there's a way to do the same with bootable USBs........:D

I vaguely remember trying it but don't think it worked, so

You need to see my other post about booting USB installs from a PC that doesn't boot from USB

[http://ubuntuforums.org/showthread.php?t=992426](http://ubuntuforums.org/showthread.php?t=992426)

---

### Post by mutantbabboo on 2011-04-26
it keeps telling me no file or directory exsists

---

### Post by DGINSD on 2011-04-30
I'm running into some issues I'm running Maverick 10.10 but I don't have a file "menu.lst" in /boot/grub/. I'm assuming I'm not supposed to be creating it.

I did find this in /etc/grub.d/40_custom which is an executable and reads:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
```

So I thought perhaps following your instructions up to adding the entry into "menu.lst" and instead adding it to the end of "40_custom" instead might work, but no cigar. What am I doing wrong or what different steps need to be taken for Maverick?

I really need this option as using the bios boot option is really hit or miss and sometimes totally unusable. Some help please? :)

---

