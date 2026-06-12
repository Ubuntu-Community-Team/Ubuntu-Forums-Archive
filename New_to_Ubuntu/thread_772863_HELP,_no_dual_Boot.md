---
title: "HELP, no dual Boot"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Gatochix on 2008-04-28
Hi,
I`m new at ubuntu and I have a serious problem.
I have installed Ubuntu on a computed that already has Windows Xp installed. Everything went perfectly but now I can´t boot Windows....
I installed Ubuntu on a 2nd disk I have and left windows in the first one.
I can`t even see the Grub.
Thanks in advance.

---

### Post by LaRoza on 2008-04-28
> **Gatochix said:**
> Hi,
I`m new at ubuntu and I have a serious problem.
I have installed Ubuntu on a computed that already has Windows Xp installed. Everything went perfectly but now I can´t boot Windows....
I installed Ubuntu on a 2nd disk I have and left windows in the first one.
I can`t even see the Grub.
Thanks in advance.

Post the output of:
```

sudo fdisk -l

```
```

cat /boot/grub/menu.lst 

```

---

### Post by Gatochix on 2008-04-30
I installed ubuntu from wubi and then I uninstalled it, but in the boot.ini there is a final code c:\wubildr.mbr="Ubuntu"  
And I can´t even boot windows just a Live CD.
I think that might be the problem, but I can´t modify boot.ini.
Thanks in advance for the help.

---

