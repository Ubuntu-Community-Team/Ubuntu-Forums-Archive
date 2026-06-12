---
title: "updates problem"
date: 2009-02-10
forum: Philippine Team
---

### Post by guitar_man on 2009-02-10
I dont if i should be called as problem...maybe it is...


I updated my machine last time,and there was an update for the kernel.
My current kernel is 2.6.24-21-generic...i updated it to 2.6.24-25,i dont remember exact the updated kernel version..I dowdload it from the update manager..then restart my machine...
PROBLEM:when Ive restarted my machine,on the GRUB boot loader the kernel version is still 2.6.24-21-generic...
it happens twice

Ive updated kernel before but updates were successful

PLEASE do help...
Thanks..

---

### Post by loell on 2009-02-10
could it be that you have multi-booted?
in my case, I have ubuntu multiboots, the latest version has the control over grub so when i boot to previous version and i update it( with kernel updates) it won't appear in menu.lst .

---

### Post by domeng on 2009-02-10
Maybe it could help if you post your /boot/grub/menu.lst here.

---

### Post by guitar_man on 2009-02-10
@domeng
default 0
timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 



@loell
nakadual-boot nga po ako sir pero dati nung nag-update ako lumulitaw sa grub ko na 2 ung kernel,tapos yung latest ang piliin ko...naedit ko na yung menu.lst at tinangal yung ibang line na lumang kernel....Qgrubeditor gnmit ko...
pero ngayong nag-update ako wala na nagpakitang latest kernel sa grub..yung .21 nalang lagi

---

### Post by guitar_man on 2009-02-10
default 0
timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro quiet splash
initrd /boot/initrd.img-2.6.24-21-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive




eto pala yung menu.lst:lolflag:
nd ko nacopy yung mS....nd ko sadya yun ha.

---

### Post by loell on 2009-02-10
can you backup your current menu.lst?

then update grub manually

```
sudo update-grub
```

the post back if theres any changes at all?

---

### Post by guitar_man on 2009-02-11
sir loell


Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

eto output...restart ko nalng...mukhang ok na e...
thanks

---

### Post by guitar_man on 2009-02-11
sir loell


la pa din nangyari...may effect kaya yung Qgrubeditor na ininstall ko...kasi dati wala nun ok naman update

---

### Post by loell on 2009-02-11
you backed up you previous menu.lst, right?

now delete it entirely ( sudo rm /boot/grub/menu.lst )

re-update grub again, then post the updated menu.lst

---

### Post by guitar_man on 2009-02-11
Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done




## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dd490430-2d21-499f-a13a-da08d4d4da5b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet



###sir mukhang nawala yung Xp ko

---

### Post by loell on 2009-02-11
> **guitar_man said:**
> 
###sir mukhang nawala yung Xp ko

exactly,  so you just have to add it

```
sudo gedit /boot/grub/menu.lst
```

at the end , just copy paste it.

```

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive


```

---

### Post by killer_d76 on 2009-02-14
pasingit lang po since were speaking about boot grub.. what if i would like to add another OS like Mac OSX (patched to work for PC).. my lappie already on dualboot with XP and i'm planning to install Mac OSX on it as well, what i was planning to do is use QParted to partition my HDD and install OSX there, if i do that how would i add OSX on boot grub menu?..

i already know how to revive the existing boot grub by running live cd.. (it was erased when i reinstalled XP) will it be the same process?

thanks!

---

### Post by loell on 2009-02-14
i think you need yaboot. :) but i really don't know how that works. :(

---

### Post by guitar_man on 2009-02-15
sir loell bakit nung 2.6.24-23-generic na yung ginamit kong kernel ayaw na gumana yung compiz fusion ko?
medyo madaming error ako nakuha...ngayon nga lang ako nakapagpost sa sa sobrang pangngalikto ng kompyuter ko

---

### Post by loell on 2009-02-15
how did you get your video drivers before? did you compile it?

---

### Post by guitar_man on 2009-02-15
hindi sir...sa add/remove ko lang yun niligay:(

---

### Post by loell on 2009-02-15
> **guitar_man said:**
> hindi sir...sa add/remove ko lang yun niligay:(

strange, i'm not sure why it would not do compiz.  in any case 2.6.24-23 and below  versions, are now available at your grub selection, try other kernel entries, see what works and what doesn't.

---

### Post by guitar_man on 2009-02-16
sir loell...
sa kernel 2.6.24-22 ok yung driver na-enable ko sa *Hardware Dirvers*

pero ayaw pa din gumana ng mga effects...hindi kaya hindi pa ok yung Video Card ko pa sa 2.6.24-23?
NVIDIA FX5200 128mb

---

### Post by loell on 2009-02-16
hmmm, really a strange case, i do have an nvidia card, and never have i encounter a symptom like this (yet).

perhaps this is a xorg issue, it may be better to make another clean thread for this. :)

---

