---
title: "I am getting &lt;initramfs&gt; prompt window when i tried booting linux"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by prasaanth on 2008-07-11
I am new to ubuntu and wanted to try it out in my system. I loaded it as a live CD of Hardy Heron and it worked perfectly, later i bought a 250Gb SATA HDD in addition to my existing Harddrive so that i can use the new one to load Ubuntu and have two operating systems (in addition to windows xp, which i am using currently). However after installing the secondary harddisk and when i tried booting Linux from the CD it ends up in an <initramfs> command prompt.
Please help me.

Thanks in advance

---

### Post by hyper_ch on 2008-07-11
when starting the install cd, you have an option to check the cd for defects... maybe it got scratched meanwhile.

---

### Post by avtolle on 2008-07-11
This has helped some folks with SATA issues on installation.

First, read this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) concerning the use of boot options. Pay attention to the part about use of boot options on installation.

Second, try to add this boot option to the boot string: all_generic_ide to be placed in the boot string as is shown for the option used as an example in the link.

Then, try to continue by booting. If this works, you should be able to install if you want after trying out the Live CD. If it doesn't work, you might want to try other boot options as are given in the link, alone at first then in combination with each other, to see whether any of them allow you to boot into the Live CD (and, don't forget the one I gave you above to use in combination with the others). This will test your patience, to be sure. Good luck.

---

