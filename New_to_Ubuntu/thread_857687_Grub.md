---
title: "Grub"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by ~alex~ on 2008-07-12
Hey guys,

I've recently installed ubuntu and I'm loving it. However my folks are slightly computer illiterate and are used to windows. This isn't a problem as I've got both operating systems still installed. The only problem is that when I turn on the PC the grub loader appears and will boot Ubuntu by default. I was wondering if it was possible to make it boot Windows by default instead? 

Cheers.

---

### Post by mevets on 2008-07-12
Yeah you can do that. You do this by editing grub's menu.list
```

sudo gedit /boot/grub/menu.lst

```
Look for a line that says
```

default 0

```
Change that number according to where Windows is in your bootloader. Realize that it starts counting at 0, so the first entry = 0 and the second entry = 1, etc.

---

### Post by NovruzeliH on 2008-07-12
mevets i gotta say, when i first started i wondered the same thing well wen i was little and i was using ubuntu 5.04 on my fathers pc :D well now got my own :D and i need xubuntu or i cant use my pc :p

---

### Post by ~alex~ on 2008-07-12
Thank you!

---

### Post by kansasnoob on 2008-07-12
Another way is to install startupmanager from synaptic.

Then you can change things easily.

---

### Post by Dr Small on 2008-07-12
> **kansasnoob said:**
> Another way is to install startupmanager from synaptic.

Then you can change things easily.
That would be the difficult way. mevets way is the simplest. :)

---

### Post by ChameleonDave on 2008-07-12
Another way to do it is to have a /boot/grub/menu.lst file similar to mine:

```

**default        saved**
timeout        11
color cyan/blue white/blue
splashimage=(hd1,6)/boot/grub/splashimages/Erin-widescreen.xpm.gz

title        Ubuntu 8.04.1
root        (hd1,6)
kernel        /vmlinuz root=LABEL=Kubuntu ro splash savedefault vga=normal
initrd        /initrd.img
**savedefault**

title XP
root (hd0,1)
chainloader +1
**savedefault**
makeactive

```My default is whatever was selected last time.

---

