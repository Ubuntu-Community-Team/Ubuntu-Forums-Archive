---
title: "[SOLVED] Reinstall GRUB on seperate partition."
date: 2008-09-17
forum: New to Ubuntu
---

### Post by skymera on 2008-09-17
Hi i just installed XP and as usual it has over written GRUB.

I need to reinstall GRUB but not sure how with different partitions.
How would i do it with the following setup?

/dev/hda1 /boot
/dev/hda2 /

Thanks :)

---

### Post by phidia on 2008-09-17
Probably the easy way to fix this is to boot from your Ubuntu install cd and choose the reinstall grub option.
Also take a look at the Ubuntu wiki on reinstalling grub [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub").

---

### Post by skymera on 2008-09-17
i followed the guide and used "grub-install" and when i reboot i get taken to a grub prompt rather than a grub menu.

How doi make it load my menu?

---

### Post by rsambuca on 2008-09-17
When using the 'grub-install' method, you still have to specify the target.  I  always find it easier to use the manual 'root', 'setup', method.

---

### Post by skymera on 2008-09-17
```
  sudo grub-install  --root-directory=/mnt/boot hd0 
```

Thats what i used, it boots grub but only the grub prompt :???:

---

### Post by rsambuca on 2008-09-17
It looks like you didn't have the correct partition mounted when you ran the command, otherwise it should be getting the stage 2 instructions from the /boot/grub directory.

---

### Post by skymera on 2008-09-17
hmm i'll double check and re run it

---

### Post by skymera on 2008-09-17
ok

I tried it. No luck.
So i downloaded SuperGRUBDisk and tried everything, it said sucessful everytine but when i boot i STILL get stuck at the GRUB command prompt? No menu loads.

But in /boot/grub/ Stage1 and Stage2 is there also menu.lst

I'm truly stumped.

Anyone can shed light on this? I'd love to use my laptop with any OS. So far its dud.

---

### Post by caljohnsmith on 2008-09-17
Just to make sure you have Grub pointing to correct partition, try the following from your Live CD:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu boot partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
```
Also, to make sure Grub can see your menu.lst:
```
grub> cat (hdX,Y)/boot/grub/menu.lst
```
Also, please post the contents of your menu.lst. If you need help with that, let me know. Otherwise let me know how it goes.

---

### Post by meierfra. on 2008-09-17
Follow caljohnsmith advice, but since you have a separate boot partition, you need to use

```
sudo find /grub/stage1
```

(instead of "find /boot/grub/stage1")


and

```
cat (hdX,Y)/grub/menu.lst
```

---

### Post by skymera on 2008-09-18
XP somehow has corrupted my Ubuntu partition.

It'a now FAT ?!? So i'll reinstall Ubuntu when Ibex is released.

Thanks for the help. Appreciate it.

---

