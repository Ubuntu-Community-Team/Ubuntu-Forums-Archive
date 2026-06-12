---
title: "Custom kernel build"
date: 2010-03-06
forum: Packaging and Compiling Programs
---

### Post by dschaefer79 on 2010-03-06
Hi,

I've tried to build a custom kernel 2.6.33 with 

fakeroot make-kpkg --revision=1 --append-to-version=x64 --initrd kernel_image kernel_headers

and it works. but after when I tried to install it with 
dpkg -i linux-image-2.6.33x64_1_amd64.deb.

I get these error :

Preparing to replace linux-image-2.6.33x64 1 (using linux-image-2.6.33x64_1_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.33x64 ...
Could not find postrm hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
Setting up linux-image-2.6.33x64 (1) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
initrd.img(/boot/initrd.img-2.6.33x64
) points to /boot/initrd.img-2.6.33x64
 (/boot/initrd.img-2.6.33x64) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.33x64.postinst line 588.
vmlinuz(/boot/vmlinuz-2.6.33x64
) points to /boot/vmlinuz-2.6.33x64
 (/boot/vmlinuz-2.6.33x64) -- doing nothing at /var/lib/dpkg/info/linux-image-2.6.33x64.postinst line 588.
Running postinst hook script update-grub.
User postinst hook script [update-grub] failed to execute: No such file or directory
dpkg: error processing linux-image-2.6.33x64 (--install):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 linux-image-2.6.33x64

Can someone help me thanks,

Dominique

---

### Post by Bachstelze on 2010-03-06
> Could not find postrm hook script [update-grub].

Apparently GRUB is not installed on your machine. How did you install Ubuntu on it?

---

