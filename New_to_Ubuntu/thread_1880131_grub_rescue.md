---
title: "grub rescue"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by tushar maroo on 2011-11-13
i had a dual install with windows 7 and ubuntu 10.04 lucid,
now somebody has deleted that partition from windows 7 where the ubuntu was install,grub menu is lost what should i do now?

---

### Post by critin on 2011-11-13
See if there's something in here to help.  

[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by raja.genupula on 2011-11-13
> **tushar maroo said:**
> i had a dual install with windows 7 and ubuntu 10.04 lucid,
now somebody has deleted that partition from windows 7 where the ubuntu was install,grub menu is lost what should i do now?

1...install ubuntu again , that will installs your grub again
 
2...[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by rng on 2011-11-13
If you are not able to boot at all, following commands typed from grub prompt may start windows: 

set root=(hd0,1)
chainloader +1
boot

---

