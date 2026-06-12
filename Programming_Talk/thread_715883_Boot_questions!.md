---
title: "Boot questions!"
date: 2008-03-05
forum: Programming Talk
---

### Post by omotto on 2008-03-05
Hi! People!

I'm working with ubuntu 7.10 and nowadays I'm involved in a new project that runs under Linux. I've downloaded the last linux kernel (2.6.23) I've compiled as:

%make xconfig

%make

then I've installed them to test under ubuntu: 

%make install

%make modules_install

I've created a new RAM FILE SYSTEM:

%mkinitramfs -o /boot/initrd.img-2.6.23.14 2.6.23.14

I've configured GRUB, writing the menu.lst file or executing the following command:

%update-grub 

All right until here! 

GRUB boots, kernel runs, the RAM FILE SYSTEM mounts and runs correctly and... 

GNOME runs!!!

NOOOO!!!!

Because I want to run my own program (like printf("hello world!\r\);) after the initialization of the modules called by RAM FILE SYSTEM!!!! Not the GNOME!!!

I want to the boot program, kernel + modules, initramfs and my program only.

Do you know how to do it?!

Thanks in advance!

---

### Post by mssever on 2008-03-05
The kernel doesn't have a whole lot to do with what runs at boot. You need to modify the bootscripts for that. Ubuntu uses Upstart nowadays to do that. I don't remember where Upstart's config lives, but since it's very new software, it mostly just runs the sysvinit files in /etc/init.d and /etc/rc[0-6].d.

---

### Post by Zwack on 2008-03-05
> **mssever said:**
> The kernel doesn't have a whole lot to do with what runs at boot. You need to modify the bootscripts for that. Ubuntu uses Upstart nowadays to do that. I don't remember where Upstart's config lives, but since it's very new software, it mostly just runs the sysvinit files in /etc/init.d and /etc/rc[0-6].d.

Exactly... You might want to replace init with your program if that's all that needs to be running...  But be very careful, more likely you want to start with a minimal init set up that runs more than just your program or you'll have to rebuild every time you have issues until you're fully finished.

Z.

---

