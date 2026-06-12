---
title: "/boot  -- what are they, how can I use them"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by cwmoser on 2008-10-17
Regarding the files in /boot

Could someone explain to me what these files are and what I can use them for?  

Will other files like those in /etc and /bin work without problems with all the different versions?

How do you roll back to an older version?

I note that there are various versions of:
[B][INDENT]config-2.6.24.*
initrd.img-2.6.24*
System.map-2.6.24*
vmlinuz-2.6.24*[/INDENT][/B]

Thanks 

Carl

---

### Post by t0p on 2008-10-17
You don't use the files in /boot at all... at least, not directly.

They are files that ubuntu uses while booting itself.

The various versions of each file are for the different kernels you have installed on your system.  For instance, look at the directory listing of my /boot:

```
t0p@ubunty:~$ ls /boot
abi-2.6.24-16-generic             initrd.img-2.6.24-19-generic.bak
abi-2.6.24-19-generic             initrd.img-2.6.24-21-generic
abi-2.6.24-21-generic             initrd.img-2.6.24-21-generic.bak
config-2.6.24-16-generic         memtest86+.bin
config-2.6.24-19-generic          System.map-2.6.24-16-generic
config-2.6.24-21-generic          System.map-2.6.24-19-generic
grub                              System.map-2.6.24-21-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-21-generic

```

The file *config-2.6.24-16-generic* relates to the kernel 2.6.24-16; *config-2.6.24-19-generic* relates to kernel 2.6.24-19... and so on.

---

### Post by bodhi.zazen on 2008-10-17
Take a look at this post : [How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817")

That should give you an overview and there are some links from there.

In a nut shell:

vmlinux is your kernel
initrd == "initial ram disk" basically mounts any drivers the kernel needs into ram.
config = the configuration file used to coplie your kernel (see [https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild))

The other files are used by Grub

See also :

[http://www.ibm.com/developerworks/linux/library/l-linuxboot/](http://www.ibm.com/developerworks/linux/library/l-linuxboot/)

[http://oldfield.wattle.id.au/luv/boot.html](http://oldfield.wattle.id.au/luv/boot.html)

(Ubuntu uses grub, LILO is an alternate boot loader and works fine, used by some distros).

---

