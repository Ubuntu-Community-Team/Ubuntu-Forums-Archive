---
title: "Upgraded to 16.04 and grub rescue appears"
date: 2017-01-05
forum: New to Ubuntu
---

### Post by storm-twister on 2017-01-05
I'm very new to Ubuntu and I'm installing v16.10 on a new drive with Win 7 already installed. I get the grub rescue prompt upon boot. The boot repair utility provided this link: 

[http://paste2.org/7aPyJEmm](http://paste2.org/7aPyJEmm)

Please help me resolve. Thank you.

---

### Post by egeezer on 2017-01-06
Try the following ..
 [INDENT]grub rescue > ls
(hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)
grub rescue > ls (hd0,msdos1) # try to recognize which partition is this
grub rescue > ls (hd0,msdos2) # let's assume this is the linux partition *
grub rescue > set root=(hd0,msdos2)
grub rescue > set prefix=(hd0,msdos2)/boot/grub # or wherever grub is installed
grub rescue > insmod normal # if this produced an error, reset root and prefix to something else ..
grub rescue > normal[/INDENT] This should fix it ..
 *Correct partition will usually be formatted as ext2

---

### Post by eionmac on 2017-01-07
You can also download to another machine Live Distro "Supergrub", burn to CD/DVD and use it to fix grub/ Regards eionmax

---

