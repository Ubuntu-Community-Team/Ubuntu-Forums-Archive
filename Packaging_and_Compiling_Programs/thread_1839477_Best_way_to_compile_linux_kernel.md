---
title: "Best way to compile linux kernel"
date: 2011-09-05
forum: Packaging and Compiling Programs
---

### Post by alegomaster on 2011-09-05
Hi, I am wondering the best way to compile the 3.0 kernel. I am using the x86-64 architecture and I use grub as the bootloader. The internet is fragmented on how to do it, so I am wondering what is the best way to do it.

I tried
```

$make old-config
$make
$sudo make modules_install
$make install
$sudo update-grub

```And it didnt work. That is why I am asking for help.

Edit: Can a mod Put this to compiling and packaging section In programming talk.

---

### Post by SevenMachines on 2011-09-08
The standard ubuntu guide is 
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
I'd follow that and see how you do

---

### Post by alegomaster on 2011-09-08
Okay, I will look into it.:)

---

