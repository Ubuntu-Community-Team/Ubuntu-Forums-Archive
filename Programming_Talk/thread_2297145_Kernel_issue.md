---
title: "Kernel issue"
date: 2015-10-01
forum: Programming Talk
---

### Post by simone22 on 2015-10-01
Hi, I am new to this forum, and new to the linux kernel compiling task.
I was trying to compile the last kernel 4.2.2 for my Lubuntu machine, following the instructions on the "Linux kernel in a nutshell" book, everything went fine until I tryed to install the compiled kernel using "sudo make install", the problem is that i recieve many errors, in particular there is this error: "depmod: ERROR: could not open directory /lib/modules/4.2.2: No such file or directory"


So when I try then to boot the new kernel in my machine I recieve many lines of that error, it says it couldn open /lib/modules/4.2.2 No such file or directory.


Here i post the error messages that I get when I run sudo make install.


giulia@giulia-pc:~/linux/linux-4.2.2$ sudo make install
[sudo] password for giulia: 
sh ./arch/x86/boot/install.sh 4.2.2 arch/x86/boot/bzImage \
	System.map "/boot"
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.2 /boot/vmlinuz-4.2.2
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.2 /boot/vmlinuz-4.2.2
update-initramfs: Generating /boot/initrd.img-4.2.2
WARNING: missing /lib/modules/4.2.2
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/4.2.2: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_elnaNd/lib/modules/4.2.2/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_elnaNd/lib/modules/4.2.2/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.2 /boot/vmlinuz-4.2.2
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.2.2 /boot/vmlinuz-4.2.2
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.2 /boot/vmlinuz-4.2.2
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.2 /boot/vmlinuz-4.2.2
Generating grub configuration file ...
Attenzione: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Trovata immagine linux: /boot/vmlinuz-4.2.2
Trovata immagine initrd: /boot/initrd.img-4.2.2
Trovata immagine linux: /boot/vmlinuz-4.2.2.old
Trovata immagine initrd: /boot/initrd.img-4.2.2
Trovata immagine linux: /boot/vmlinuz-3.19.0-30-generic
Trovata immagine initrd: /boot/initrd.img-3.19.0-30-generic
Trovata immagine linux: /boot/vmlinuz-3.19.0-29-generic
Trovata immagine initrd: /boot/initrd.img-3.19.0-29-generic
Trovata immagine linux: /boot/vmlinuz-3.19.0-28-generic
Trovata immagine initrd: /boot/initrd.img-3.19.0-28-generic
Trovata immagine linux: /boot/vmlinuz-3.19.0-27-generic
Trovata immagine initrd: /boot/initrd.img-3.19.0-27-generic
Trovata immagine linux: /boot/vmlinuz-3.19.0-26-generic
Trovata immagine initrd: /boot/initrd.img-3.19.0-26-generic
Trovata immagine linux: /boot/vmlinuz-3.19.0-23-generic
Trovata immagine initrd: /boot/initrd.img-3.19.0-23-generic
Trovata immagine linux: /boot/vmlinuz-3.19.0-22-generic
Trovata immagine initrd: /boot/initrd.img-3.19.0-22-generic
Trovata immagine linux: /boot/vmlinuz-3.16.0-38-generic
Trovata immagine initrd: /boot/initrd.img-3.16.0-38-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Trovato unknown Linux distribution su /dev/sda3
fatto




The problem is that some times the machine booted with the new kernel freezes on the lubuntu loading screen, and when I can successfully boot the network drivers doesnt work ( I have been very careful to include them properly before compiling using "make menuconfig"


Thank you in advance for your help.

---

