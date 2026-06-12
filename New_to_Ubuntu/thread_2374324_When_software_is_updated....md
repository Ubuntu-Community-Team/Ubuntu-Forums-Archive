---
title: "When software is updated..."
date: 2017-10-14
forum: New to Ubuntu
---

### Post by Innernet on 2017-10-14
Hi.
Does updating ends installations with deleting replaced files, as to cleanup discarding obsolete/useless/old files to not pile up taking space in the hard drive ?

---

### Post by Bucky Ball on 2017-10-14
If I understand you correctly, you may want:

```
sudo apt autoremove
```

That should get rid of most cruft. There are other things like 'clean' 'autoclean' and even GUI based apps like Bleach Bit, but I generally just use the autoremove command. Other forum members will have further and more specific suggestions to contribute no doubt. ;)

---

### Post by Innernet on 2017-10-14
Thanks.  OK, that takes care of it manually.  And it has to be done periodically with the posted command, or the command stays permanently aware and takes care of 'cleaning' **every time** when there is 'dirt' accumulated ? ;  "autoremove" sounds/seems like will always be doing it when necessary...

What about the original question; does it happen or supposed to happen automatically at the end of installed updates process ?   In other words, does the software updating process ends with that 'autoremove' command ?

---

### Post by Geoffrey_Arndt on 2017-10-15
No . . updates of the installed OS only updates the files specified in the update details.   Some are programs, some are libraries, etc.   It does not run cleanup routines.    Generally, . . . there is no need to do that.   Linux is not Windows.

---

### Post by gordintoronto on 2017-10-15
Another useful command:
sudo apt clean

Which removes the .deb files downloaded during updating.

---

### Post by Innernet on 2017-10-16
Hi.  Am the goofing champion...

[ATTACH=CONFIG]277137[/ATTACH]

---

### Post by mastablasta on 2017-10-16
try:
```
sudo apt-get autoremove
```

---

### Post by Innernet on 2017-10-16
The difference in precision assistance.  Thanks, Mastablasta.

Done.  Do you see abnormalities in the following ?  

```
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get autoremove
[sudo] password for externet: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.13.0-126 linux-headers-3.13.0-126-generic
  linux-image-3.13.0-126-generic linux-image-extra-3.13.0-126-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 224 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 509442 files and directories currently installed.)
Removing linux-headers-3.13.0-126-generic (3.13.0-126.175) ...
Removing linux-headers-3.13.0-126 (3.13.0-126.175) ...
Removing linux-image-extra-3.13.0-126-generic (3.13.0-126.175) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-126-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-133-generic
Found initrd image: /boot/initrd.img-3.13.0-133-generic
Found linux image: /boot/vmlinuz-3.13.0-132-generic
Found initrd image: /boot/initrd.img-3.13.0-132-generic
Found linux image: /boot/vmlinuz-3.13.0-129-generic
Found initrd image: /boot/initrd.img-3.13.0-129-generic
Found linux image: /boot/vmlinuz-3.13.0-128-generic
Found initrd image: /boot/initrd.img-3.13.0-128-generic
Found linux image: /boot/vmlinuz-3.13.0-126-generic
Found initrd image: /boot/initrd.img-3.13.0-126-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-70-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-3.13.0-126-generic (3.13.0-126.175) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
dkms: removing: nvidia-304 304.128 (3.13.0-126-generic) (i686)

-------- Uninstall Beginning --------
Module:  nvidia-304
Version: 304.128
Kernel:  3.13.0-126-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_304.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-126-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-126-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-126-generic /boot/vmlinuz-3.13.0-126-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-133-generic
Found initrd image: /boot/initrd.img-3.13.0-133-generic
Found linux image: /boot/vmlinuz-3.13.0-132-generic
Found initrd image: /boot/initrd.img-3.13.0-132-generic
Found linux image: /boot/vmlinuz-3.13.0-129-generic
Found initrd image: /boot/initrd.img-3.13.0-129-generic
Found linux image: /boot/vmlinuz-3.13.0-128-generic
Found initrd image: /boot/initrd.img-3.13.0-128-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-70-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
externet@externet-Compaq-Presario-CQ60-Notebook-PC:~$
```

---

### Post by deadflowr on 2017-10-16
> Do you see abnormalities in the following ? 

<snip>
Output is as expected.
No errors.
You're good to go.

---

