---
title: "Move &amp; resize /boot without messing up the system"
date: 2016-11-12
forum: New to Ubuntu
---

### Post by mkohan on 2016-11-12
Hi,
I am a windows refugee trying to migrate to Ubuntu while keeping Win10 as a fall back on atiny partition. I want to update my Trusty to 16.04 but the boot (sda6) partition seems to be a little bit too small (pic). How exactly could I move and resize boot without messing up anything? And should I also enlarge the root (sda7)? Home is large enough I guess...
(GParted running on Elementary Live USB)

---

### Post by ian-weisser on 2016-11-12
Why do you feel your /boot partition on sda6 is too small?
Seems fine to me.

---

### Post by mkohan on 2016-11-12
I share your views, but sadly, Distribution Updater does not... around 1MB is missing for him.

---

### Post by ian-weisser on 2016-11-12
Remove an old kernel using apt. That will free up much more than 1MB, and is much easier than repartitioning.

Example:
```
me@me:~$ uname -r
**4.8.0-26-generic**          // This is the currently running kernel. Don't delete it.

me@me:~$ ls /boot
abi-4.8.0-26-generic         memtest86+.elf
abi-4.8.0-27-generic         memtest86+_multiboot.bin
config-4.8.0-26-generic      System.map-4.8.0-26-generic
config-4.8.0-27-generic      System.map-4.8.0-27-generic
grub                         vmlinuz-4.8.0-26-generic
**initrd.img-4.8.0-26-generic**  vmlinuz-4.8.0-26-generic.efi.signed
**initrd.img-4.8.0-27-generic**  vmlinuz-4.8.0-27-generic
memtest86+.bin               vmlinuz-4.8.0-27-generic.efi.signed
```

In this case, I can reboot into the -27 kernel, verify that all functions properly, then use apt to remove the -26 kernel.

---

### Post by mkohan on 2016-11-12
Amazeballs! Solved. Have all my accessible thanks. :)

---

### Post by wildmanne39 on 2016-11-12
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

