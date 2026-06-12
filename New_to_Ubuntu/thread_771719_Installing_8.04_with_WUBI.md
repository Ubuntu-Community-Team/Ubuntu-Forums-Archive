---
title: "Installing 8.04 with WUBI"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Cirdan Alcarin on 2008-04-27
Hi I tried installing 8.04 with the new WUBI but once I go through the entire installation and I choose to load Ubuntu from the boot loader I get this error 

"Booting Ubuntu 8.04, kernel 2.6.24-16-generic

file system type is NTFS, partition type 0x7
kernal /boot/vmlinuz-2.6.24-16-generic
root=UUID=6ac1f425ff4780eb
loop=/ubuntu/disks/root.disk ro quiet
splash

Error 15: file not found"

Any ideas on how to fix this? or what this means exactly?

---

### Post by Paqman on 2008-04-27
Seems like the bootloader isn't finding the kernel.

Looks like [you're not the first person to see that error code](http://ubuntuforums.org/showthread.php?t=759816). I'm no expert, but they seem to be talking about how the drives are numbered in that thread. Have you go Wubi installed on C drive?

---

### Post by Cirdan Alcarin on 2008-04-27
I believe so, I have the Ubuntu folder on the C drive, my HD layout is I have two drives on the primary IDE channel and I have another HD connected via sata.  The SATA drive is my primary drive (C)

---

