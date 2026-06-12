---
title: "Cleaning up /boot"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by mjd95 on 2013-06-14
I'm using ubuntu precise, and "uname -a" outputs
```

Linux math-pc552 3.2.0-45-generic #70-Ubuntu SMP Wed May 29 20:12:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```
I didn't set up this machine, but I do have full administrator access on it.

I just received a warning message from ubuntu saying that /boot was almost full (<11MB left); the output of "ls -a" in that directory is
```

  777 abi-3.2.0-23-generic    138 config-3.2.0-23-generic      5 grub                         14527 initrd.img-3.2.0-48-generic   2836 System.map-3.2.0-43-generic   4879 vmlinuz-3.2.0-43-generic
  779 abi-3.2.0-38-generic    139 config-3.2.0-38-generic  14465 initrd.img-3.2.0-23-generic     12 lost+found                    2837 System.map-3.2.0-44-generic   4880 vmlinuz-3.2.0-44-generic
  779 abi-3.2.0-39-generic    139 config-3.2.0-39-generic  14483 initrd.img-3.2.0-38-generic    174 memtest86+.bin                2837 System.map-3.2.0-45-generic   4880 vmlinuz-3.2.0-45-generic
  781 abi-3.2.0-40-generic    139 config-3.2.0-40-generic  14485 initrd.img-3.2.0-39-generic    176 memtest86+_multiboot.bin      2838 System.map-3.2.0-48-generic   4882 vmlinuz-3.2.0-48-generic
  781 abi-3.2.0-41-generic    139 config-3.2.0-41-generic  14526 initrd.img-3.2.0-40-generic   2829 System.map-3.2.0-23-generic   4870 vmlinuz-3.2.0-23-generic
  781 abi-3.2.0-43-generic    139 config-3.2.0-43-generic  14527 initrd.img-3.2.0-41-generic   2832 System.map-3.2.0-38-generic   4873 vmlinuz-3.2.0-38-generic
  781 abi-3.2.0-44-generic    139 config-3.2.0-44-generic  14527 initrd.img-3.2.0-43-generic   2833 System.map-3.2.0-39-generic   4875 vmlinuz-3.2.0-39-generic
  781 abi-3.2.0-45-generic    139 config-3.2.0-45-generic  14528 initrd.img-3.2.0-44-generic   2835 System.map-3.2.0-40-generic   4879 vmlinuz-3.2.0-40-generic
  781 abi-3.2.0-48-generic    139 config-3.2.0-48-generic  14527 initrd.img-3.2.0-45-generic   2836 System.map-3.2.0-41-generic   4879 vmlinuz-3.2.0-41-generic

```
I would like to make some more space in here.  I guess I shouldn't touch anything in /boot/grub, but would I be okay to delete things of the form "*-3.2.0-x", where x<45?  (I am also confused why some of these have x=48 but my kernel is x=45, but that's a secondary concern.)  Furthermore, would there be a way to automate this, so that I don't have to do this everytime /boot gets full?

Thanks in advance.

---

### Post by slickymaster on 2013-06-14
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")
[Automating removal of old kernels]("http://ubuntuforums.org/showthread.php?t=1961409http://ubuntuforums.org/showthread.php?t=1961409")

---

### Post by Impavidus on 2013-06-14
Use slickymaster's link to uninstall some old kernels. Keep 45 and 48.

I installed 48 this morning. Maybe you just installed it too and hadn't rebooted yet? That would explain why 48 is there whilst you're running 45.

---

### Post by mjd95 on 2013-06-14
Great, and that makes sense, thanks to both of you.

---

