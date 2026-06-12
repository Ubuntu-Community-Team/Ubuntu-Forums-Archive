---
title: "grub bootloader"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by atif.iu on 2008-07-05
can anyone help me.....i m a new fan of linux....i hve installed open suse and ubuntu8.04 on my laptop with vista and xp....i dont get the option of xp in grub bootloader...and click on vista i get vista bootloader from where i can boot to vista but not to xp....what should i do...to get the option of xp...in grub

---

### Post by sharks on 2008-07-05
this may help u:
go to terminal and type **gedit /boot/grub/menu.lst** and add the following:


> title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

you need to do this because windows doesn`t boot from the secondary IDE,
the entry to boot my windows partition is
Code:

title Windows
root (hd0,1)
chainloader +1


i think that u have only one hard drive.

---

### Post by stoneybroke on 2008-07-05
If you installed windows first then ubuntu the boot screen would have given you the choice so now insert the ubuntu installer cd and re-boot the bootloader can be got at here sudo gedit /boot/grub/menu.lst and there is a tutorial for grub here [http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/) that you should find interesting.

Hope that helps

---

### Post by Elfy on 2008-07-05
You are going to need to provide asome details of your partitions, this command will do

```
sudo fdisk -l
```

Don't run the command above it should be 

```
gksudo gedit /boot/grub/menu.lst
```

also is the boot list on ubuntu or suse, if you installed buntu l;ast that is where it will be. Not usre if opensuse uses the same bootloader, only played with it for a while.

---

