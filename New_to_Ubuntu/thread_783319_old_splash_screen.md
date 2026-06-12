---
title: "old splash screen"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-05
I miss the splash screen in Dapper Drake (specifically how it would show the details of what was loading such as loading RAID devices or whatever).  Anyway, does anyone know how to enable this in Hardy?  <ocd>(I really liked making sure that everything works on bootup)</ocd>

---

### Post by pro003 on 2008-05-05
this is probably stupid idea, and am not saying you should try but once I have deleted swap and every time I was starting ubuntu I had everything going in front of my eyes just like you said... but am sure there's a more painless way to reach to that...:lolflag:

---

### Post by plucky on 2008-05-05
Never used Dapper but try this.

```
gksudo gedit /boot/grub/menu.lst
```

Search for the lines that look like this

> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=125bc66f-c84c-41b8-9d91-3ca866cb4800 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet


and change it to > title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=125bc66f-c84c-41b8-9d91-3ca866cb4800 ro splash
initrd		/boot/initrd.img-2.6.24-16-generic

this i.e remove the word **quiet** And also to keep it this way after a kernel upgrade,search for > # defoptions=quiet splash and again remove quiet.DO NOT REMOVE THE #.

Good Luck

---

### Post by fontenot_1031 on 2008-05-06
> **plucky said:**
> Never used Dapper but try this.

```
gksudo gedit /boot/grub/menu.lst
```

Search for the lines that look like this




and change it to 

this i.e remove the word **quiet** And also to keep it this way after a kernel upgrade,search for  and again remove quiet.DO NOT REMOVE THE #.

Good Luck

Thanks man!  I can't wait to try this out!

---

