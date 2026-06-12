---
title: "Running a new kernel, kernel panic"
date: 2017-04-15
forum: Packaging and Compiling Programs
---

### Post by albocoder on 2017-04-15
Hi all,
I recently wanted to compile my kernel and make it run. I would like to know what steps are going wrong in my logic.


1) Check the architecture using ```
uname -a
```. Mine is x86_64 
2) head over to linux-4.4.1 kernel source and in shell type ```
make ARCH=x86_64 defconfig
```. 
3) Then make the new kernel ```
make -j 40 ARCH=x86_64
```
4) After waiting for some time i got the message the kernel is at /arch/x86/boot/bzImage
5) then I did ```
sudo cp bzImage /boot/vmlinuz-4.4.1-1-generic
```. (This renaming was purely of my intuition)
6) sudo update-grub
7) restart to grub and choose the new kernel from the list


However I get this:

[IMG]https://preview.ibb.co/mtaZ35/17965451_2243665222526027_1420364506_n.png[/IMG]

---

### Post by howefield on 2017-04-15
Moved to the "*Packaging and Compiling Programs*" forum.

---

### Post by albocoder on 2017-04-16
*bump*

---

