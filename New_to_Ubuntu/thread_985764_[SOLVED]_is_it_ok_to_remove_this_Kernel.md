---
title: "[SOLVED] is it ok to remove this Kernel"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by newbee70 on 2008-11-17
After the kernel update I now have this on my loader screen at boot up,

Is it safe to uninstall 2.6.24.19 from my system or is it still necessary
for proper operation?


XXXXXXXX@desktop2:~$ ls /boot
abi-2.6.24-19-generic     initrd.img-2.6.24-19-generic      System.map-2.6.24-19-generic
abi-2.6.24-21-generic     initrd.img-2.6.24-19-generic.bak  System.map-2.6.24-21-generic
config-2.6.24-19-generic  initrd.img-2.6.24-21-generic      vmlinuz-2.6.24-19-generic
config-2.6.24-21-generic  initrd.img-2.6.24-21-generic.bak  vmlinuz-2.6.24-21-generic
grub                      memtest86+.bin
YYYYYY@desktop2:~$

---

### Post by BGFG on 2008-11-17
I asked this same question a while back :) once you have updated to the new kernel, and you can verify which one by running
```

uname -a

```
in the terminal, then it's safe to remove the old kernel. i usually leave an extra one there just in case.

[http://ubuntuforums.org/showthread.php?t=852807](http://ubuntuforums.org/showthread.php?t=852807)

---

### Post by newbee70 on 2008-11-17
> **BGFG said:**
> I asked this same question a while back :) once you have updated to the new kernel, and you can verify which one by running
```

uname -a

```
in the terminal, then it's safe to remove the old kernel. i usually leave an extra one there just in case.

[http://ubuntuforums.org/showthread.php?t=852807](http://ubuntuforums.org/showthread.php?t=852807)


Thanks for the info; I searched the forums for kernel and didn't get any results 

I will mark this as solved

---

### Post by BGFG on 2008-11-18
Yeah, sometimes the search doesn't really give proper hits. Glad i could help....

---

