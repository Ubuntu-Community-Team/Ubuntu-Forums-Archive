---
title: "What worked for me installing Lubuntu 13.10 on IBM T20"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by crenvy54 on 2014-02-25
I'm posting this because all the other solutions I found wrt problems booting from a USB stick didn't apply, and booting from DVD didn't work, but I found a way to do it as a CD install. If you are restoring an old computer such as the T20, you will find that the BIOS doesn't support booting from a USB drive, so you have to use a network boot or the optical drive.

Most solutions say that for a USB boot you must change isolinux -> syslinux and vice versa. In my case, isolinux was not recognized at boot time and gave the infamous "no default or uid ... blah" error. Actually changing isolinux->syslinux using a DVD install got somewhere but failed later in the install. 

This T20 actually has a DVD-ROM drive, but I found that making the above directory name change AND using a CD instead of a DVD disk made the difference. 

So, one more workaround you may not have seen before. 

Cheers,

Casey

---

### Post by zvacet on 2014-02-25
If you can not boot from usb and you can boot from optical drive here is good trick.Download [Plop.]("http://www.plop.at/en/ploplinux/download.html") Burn iso  on CD and then boot from that CD.You will find option to boot from usb inside.Use it and your comp will never see the difference.Enjoy! ;)

---

