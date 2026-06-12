---
title: "grub dual boot help."
date: 2008-08-03
forum: Other OS Talk
---

### Post by DieselNut on 2008-08-03
ok, so here it goes. I am still noobish at linux, so please bear with me. I am trying to dual boot my computer. I have two seperate drives. The master drive has Gentoo loaded on it. It is 120 gigs. On my other drive I have debian. The debian drive is 20 gigs and is the slave. The problem is when I go see the grub boot screen I see both distros. I see the debian and I see the gentoo. To be exact the grub list reads as this:

```

Debian GNU/Linux, kernel 2.6.18-6-k7
Debian GNU/Linux, kernel 2.6.18-6-k7 (single-user mode)
Other Operating system:
Gentoo Base System release 1.12.11.1 (on /dev/hda1)

```


So the problem I have is that the gentoo option wont load. When selected I get this: 
```

   Booting 'Gentoo Base System release 1.12.11.1 (on /dev/hda1)'
root  (hd0,0) 
   Filesystem type is ext2fs, partition type 0x83
kernel   /boot/kernel-gnekernel-x86-2.6.24-gentoo-r5 root=dev/ram0 init=/linuxr c ramdisk=8192 real_root=dev/sda1

Error 2: bad file or directory type 

Press any key to continue...
```

So thats it. Like I said, Im still noobish, but I am very willing to learn linux. SO far, with debian, I love it and dont want to really ditch it for gentoo. 

Other info: GNU GRUB version 0.97



SO, please help me with this, I know Im not running ubuntu, but debian is pretty close.:)

---

### Post by Rocket2DMn on 2008-08-03
Moved to Other OS Talk

---

### Post by ajmorris on 2008-08-03
> **DieselNut said:**
> 
```

   Booting 'Gentoo Base System release 1.12.11.1 (on /dev/hda1)'
root  (hd0,0) 
   Filesystem type is ext2fs, partition type 0x83
kernel   /boot/kernel-gnekernel-x86-2.6.24-gentoo-r5 root=dev/ram0 init=/linuxr c ramdisk=8192 real_root=dev/sda1

Error 2: bad file or directory type 

Press any key to continue...
```So thats it. Like I said, Im still noobish, but I am very willing to learn linux. SO far, with debian, I love it and dont want to really ditch it for gentoo. 


Hi there,
try changing your kernel line to:
```
kernel   /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda1
```
Be careful, i changed where your kernel is pointing to, '**gen**kernel' that is what the gentoo gen kernel script generates, i assumed you hadnt renamed it
AJ

---

### Post by DieselNut on 2008-08-03
> **ajmorris said:**
> Hi there,
try changing your kernel line to:
```
kernel   /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda1
```
Be careful, i changed where your kernel is pointing to, '**gen**kernel' that is what the gentoo gen kernel script generates, i assumed you hadnt renamed it
AJ
Hey, thanks for your reply. I changed the gne to gen, but still  nothing. same error.:(

---

### Post by ajmorris on 2008-08-03
> **DieselNut said:**
> Hey, thanks for your reply. I changed the gne to gen, but still  nothing. same error.:(

did you change the other parts i changed?
just copy the whole line i posted and replace yours with it.

BTW, upon editing your menu.lst file, it is a good idea to back it up first

AJ

---

### Post by tommcd on 2008-08-03
See post #4 from this thread to boot any distro from grub's interactive mode:
[http://ubuntuforums.org/showthread.php?t=393379](http://ubuntuforums.org/showthread.php?t=393379)

---

### Post by louieb on 2008-08-03
Don't know much about Gentoo. Just wondering if you have GRUB installed inside of it? If so you can get Debian's' GRUB program to use Gentoo's GRUB configuration file like this.

```
title Use Gentoo GRUB configuration file
configfile (hd0,0)/boot/grub/menu.lst  
```

Of course you have to replace /boot/grub/menu.lst with whatever Gentoo names its GRUB configuration file.

---

### Post by RaeNye on 2008-10-12
The same bug was biting me for a few hours before I found out that grub 0.97 doesn't like newly created ext3 partitions since they have 256-byte inodes. 

More info [here](http://www.linuxplanet.com/linuxplanet/tutorials/6480/1/).

---

