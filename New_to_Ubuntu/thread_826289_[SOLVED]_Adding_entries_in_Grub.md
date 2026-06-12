---
title: "[SOLVED] Adding entries in Grub?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by DBrocks on 2008-06-11
Hey guys,

I'm trying to add G4L to the Grub boot menu so I don't need to use a CD to boot into it. So, i copied the contents of the G4L cd into "/boot/g4l". (I have a seperate boot partition (/dev/sda1), because my 500gb HDD cant be booted to by my ancient BIOS. lol. In /dev/sda1, i have the /boot. in '/boot' i have a directory 'g4l' where i have all the stuff ie: isolinux.bin, ramdisk.gz. So here's my grub menu.lst


```
## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.24-16-generic root=UUID=11cf348e-8785-404f-990b-d39623a5d6e8 ro quiet splash
initrd          /initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.24-16-generic root=UUID=11cf348e-8785-404f-990b-d39623a5d6e8 ro single
initrd          /initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

title          G4L
root           (hd0,0)
kernel         /g4l/isolinux.bin root=/dev/sda1

quiet
### END DEBIAN AUTOMAGIC KERNELS LIST

```

But i get an error saying 'invalid or unsupported executeable format' what does this mean? that a BIN can't be booted?

---

### Post by gr4nf on 2008-06-11
It looks like it's already there. Am i missing something?

---

### Post by DBrocks on 2008-06-11
It is in use... when i try and boot it, it dies. lol :lolflag:

---

### Post by Joeb454 on 2008-06-11
I don't think you can boot the BIN file, I've never found anything that suggests you can boot them either :)

---

### Post by Duck2006 on 2008-06-11
You can try.

title          G4L
root           (hd0,0)
chainloader +1

But i think you will address it better as it is booting from your ubuntu partition. Can you make a nother partition just for G4l and boot it from there?

---

### Post by DBrocks on 2008-06-11
Still no luck.

---

### Post by meierfra. on 2008-06-11
Try this

```
title G4L
root (hd0,0)
kernel  /g4l/bz25.3 ramdisk_size=65536 root=/dev/ram0 noacpi
initrd  /g4l/ramdisk.gz
```


But make sure that you have the files bz25.3 and /ramdisk.gz in /boot/g4l.

If this does not work look at the file "isolinux.cfg" in /boot/g4l.  It will give you some other options. isolinux uses a different format than grub, but looking at the example I gave you, you should be able to translate from "isolinux" to "grub".

---

### Post by meierfra. on 2008-06-11
One more thing, move your "g4l" entry below the line

### END DEBIAN AUTOMAGIC KERNELS LIST

Otherwise it will disappear after the next  ubuntu kernel update.

---

### Post by DBrocks on 2008-06-11
Meiferra: Worked like a charm! Thanks a million!:guitar:

---

