---
title: "Kernels &amp; Updates"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Pudworthy on 2008-06-23
Ok...

So I updated to 2.6.24-19 last week, and now I'm not sure what I'm supposed to do...

My boot loader now has goodness knows how many entries, and I'm not sure of the relevance of each. Using KGrubEditor I can see I have my old entries of Ubuntu 2.6.24-18, and that works fine, but now I also have the Debian GNU/Linux 2.6.24-19 appearing. When I try to load it, it goes into Ubuntu but often crashes out. Plus it doesn't have the usual plush loading screens...

Forgive me for my newness, but I don't have a clue what's what here.

Thanks in advance!

---

### Post by aheckler on 2008-06-23
Please post the output of "cat /boot/grub/menu.lst"

---

### Post by Duck2006 on 2008-06-23
You can edit your menu.lst with a

# in front of the kernels line that you don't want to show,

or you can go to your Synaptic Package Manager and search for

kernel-image

and remove them from there.

---

### Post by Pudworthy on 2008-06-23
title Linux Ubuntu 8.04
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=f3e5c4ce-f0e0-483c-9ce5-bdee6dd07f7f ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic

title Linux Ubuntu 8.04 (Recovery Mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=f3e5c4ce-f0e0-483c-9ce5-bdee6dd07f7f ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin

title Other operating systems:

title Windows Vista
root (hd0,0)
chainloader +1
savedefault
makeactive

title Debian GNU/Linux, kernel 2.6.24-19-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sdb1 ro
initrd /boot/initrd.img-2.6.24-19-generic

title Debian GNU/Linux, kernel 2.6.24-19-generic (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sdb1 ro single
initrd /boot/initrd.img-2.6.24-19-generic

Ok, hope that's what you needed

And I can rename things, and delete them if need be, I just don't know what they are.

Thanks again, P

---

### Post by howlingmadhowie on 2008-06-23
where did you get that kernel from? 

can you post the contents of
/etc/apt/sources.list

---

### Post by Pudworthy on 2008-06-23
Heck, I wish I wasn't such a newbie...

Post the contents of what now?

P

---

### Post by the_doc on 2008-06-23
**cat /etc/apt/sources.list** in a terminal then copy and paste.

or

**cat /etc/apt/sources.list > output.txt** in a terminal then open output.txt then copy and paste.

---

### Post by Pudworthy on 2008-06-23
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


Erm... there's alot there...

Hope it's what you needed...

P

---

### Post by Duck2006 on 2008-06-23
Did you ever have Debian install at any time?

---

### Post by Nepherte on 2008-06-23
You can specify the number of kernels listed in grub with the option #howmany in /boot/grub/menu.lst. By default that option is #howmany=all. You can replace all with the number of kernels you'd like to see. As for the kernel entries themselves, "Debian GNU/Linux, kernel 2.6.24-19-generic" is a bit odd, since I guess you don't use debian. Your sources.list file only shows ubuntu repositories though.

---

### Post by barney385 on 2008-06-23
I had the same problem with the 19 upgrade kernel. I didn't install **ALL** of the upgrades that were available and that is what caused me problems...

As soon as I did a full upgrade everything was fine.

:smile:

---

### Post by Pudworthy on 2008-06-23
Hmm...

Thanks for the replies and the help.

I'm substantially glad i'd not done something stupid, this is actually a weird thing... *phew*

Well I've never installed Debian, and I'm pretty certain I installed all of the options when it came time to upgrade.

Should I just ignore it and use my existing boot entry as normal?

P

---

### Post by Duck2006 on 2008-06-23
> **Pudworthy said:**
> Hmm...

Thanks for the replies and the help.

I'm substantially glad i'd not done something stupid, this is actually a weird thing... *phew*

Well I've never installed Debian, and I'm pretty certain I installed all of the options when it came time to upgrade.

Should I just ignore it and use my existing boot entry as normal?

P

If it's not giving you trouble then yes. If you don't want to see it at boot up time then edit your menu.lst and # the line out.

---

### Post by Pudworthy on 2008-06-23
Ok, great, that's what I was hoping. Thanks again, chums.

In the meantime, the fact that my normal boot is still -18, is that fine?

P

---

### Post by philinux on 2008-06-23
Just do this in the terminal.

sudo apt-get update && sudo apt-get upgrade

Hopefully it will not show any errors.

---

### Post by aheckler on 2008-06-23
> **Pudworthy said:**
> In the meantime, the fact that my normal boot is still -18, is that fine?

You should be fine.

---

