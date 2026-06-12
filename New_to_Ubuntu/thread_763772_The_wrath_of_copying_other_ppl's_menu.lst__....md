---
title: "The wrath of copying other ppl's menu.lst  ..."
date: 2008-04-23
forum: New to Ubuntu
---

### Post by pprince on 2008-04-23
at first, after i've updated ubuntu[7.10], i found that the xp option has gone, so i copy other ppl's menu.lst, well, i can get into xp again but now i cant get into ubuntu bcoz of it's boot setting, here's the progress i tried to recover it after searched in google for long time...
0)cat /boot/grub/menu.lst (I found the setting is "root (hd0,6)")
1)fine /boot/grub/stage  (it reply :"root (hd0,2)")
2)
  "root (hd0,2)"
  "setup (hd0)" [ALL OK]
3)so i press e and edit "root (hd0,6)" to "root (hd0,2)"
4)after that i tried to boot but there's an error:
  error 15:file not found

that's all i can do, and i dunno what to do for next
there's a backup of menu.lst(which can get in ubuntu but not xp)
located at ubuntu's desktop

now what should i do? i've search in google all day long but still cannot fix it lol...  plz help!

---

### Post by philinux on 2008-04-23
Best bet sounds like reinstall grub from the live cd.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by aeiah on 2008-04-23
you could access your ubuntu partitions from windows if you install the ext2/ext3 drivers for windows
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

---

### Post by Oldsoldier2003 on 2008-04-23
you could burn a  [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/") and let supergrub fix it for you.

---

### Post by MrEgg on 2008-04-23
Hi,

Tell me if I get this straight. You currently have two different versions of menu.lst, one of which lets you access Ubuntu, and the other lets you access Windows? If you boot from a live cd, can you mount your Ubuntu partition and access your menu.lst? If your answer is yes to both of my questions, then can you post 1) both versions of ```
/boot/grub/menu.lst
``` (letting us know which lets you do what), 2) the output of ```
cat /proc/partitions
``` and 3) the output of ```
df
``` If everything works separately, it should be possible to put it back together.

Cheers,
Egg

---

