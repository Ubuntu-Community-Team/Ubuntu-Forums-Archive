---
title: "boot questions!"
date: 2008-03-05
forum: Packaging and Compiling Programs
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

I want the boot program, kernel + modules, initramfs and my program only.

Do you know how to do it?!


Thanks in advance!

---

### Post by jaddle on 2008-03-07
If you want to run a specific program when the computer starts up, and NOTHING else, you probably just want to replace init. Easiest way would be to just stick in a new setting to the boot prompt in grub's menu.lst. From the bootprompt howto ([http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html](http://tldp.org/HOWTO/BootPrompt-HOWTO-3.html)) I see this:

> 
The `init=' Argument

The kernel defaults to starting the `init' program at boot, which then takes care of setting up the computer for users via launching getty programs, running `rc' scripts and the like. The kernel first looks for /sbin/init, then /etc/init (depreciated), and as a last resort, it will try to use /bin/sh (possibly on /etc/rc). If for example, your init program got corrupted and thus stopped you from being able to boot, you could simply use the boot prompt init=/bin/sh which would drop you directly into a shell at boot, allowing you to replace the corrupted program.


So you could put any other command there as well - init=/bin/mylittleprogramthatdoeswhateverIwantitto. Then no daemons will start, none of your /etc/init.d scripts will run, nothing in /etc/fstab will be mounted, etc.. That may or may not be what you want.

Of course, if you just want the computer to start without gnome, you can always just uninstall gnome. :)

---

