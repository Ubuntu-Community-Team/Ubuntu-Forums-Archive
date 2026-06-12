---
title: "Unable to install GRUB on software RAID"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Nick_Short on 2014-02-25
[FONT=arial]Hi All,

I'm absolutely new to Linux, trying to install Ubuntu 13.10 from a CD onto a Dell Dimension 9200 to replace Windows XP. Everything goes fine until I get a message saying "Unable to install GRUB in /dev/sda: Executing 'grub-install/dev/sda' failed. This is a fatal error.[COLOR=#333333]" [/COLOR]

[COLOR=#333333]I've tried installing GRUB on each of the other alternatives it then offers, with no success. I've tried Boot-repair, which makes some changes ([http://paste.ubuntu.com/6993506](http://paste.ubuntu.com/6993506) & 6993758) but still leaves the machine unable to boot. And running ls /dev/m* from the terminal window left me no wiser about where to install the GRUB.
[/COLOR][/FONT][FONT=UbuntuRegular][COLOR=#333333][FONT=arial]
I've got no need to keep a dual boot with Windows, as I'm trying to convert to Ubuntu. I think the problem may be that the hard disk is actually two 149 GB drives configured as a RAID0 with fakeRAID or software RAID (most likely the latter if I understand correctly, but I'm not even sure how to tell reliably). If it is, I know there are many posts about this type of thing, but the problem is that they don't all seem to agree and most of them suggest solutions I simply have no idea how to do yet.

Any help would be very much appreciated!

Thanks a lot, Nick[/FONT]
[/COLOR][/FONT]

---

### Post by cprofitt on 2014-02-25
Can you undo the raid?

---

