---
title: "[SOLVED] new kernel not showing up in grub"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Theo148 on 2008-05-31
I have updated to the new kernel (2.6.24-17), but for some reason it refused to show up in grub's menu on startup. Running 'update-grub' outputs:

```
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

It seems to have run properly, but for some reason the kernel list is still not updated. :confused: I've attached my menu.lst file - as you can see the new kernel version is still missing from it.

Any help would be greatly appreciated.

---

### Post by shifty_powers on 2008-05-31
what happens if you go into synaptic and search for 2.6.24-17

---

### Post by bwhite82 on 2008-05-31
I've attached a correctly modified menu.lst for you. I left in the old kernel just in case you have problems with the new. If everything is working fine with the new kernel, you can remove the old in Synaptic. Additionally, I would file a bug report for 'update-grub'.

---

### Post by philinux on 2008-05-31
You could also install startupmanager and set it to display only 1 kernel.

Old ones have a use if the system borks.

---

### Post by wariskampar on 2008-05-31
i agree with SoldierBoy. I face similar problem before and only manage to get through it by manually edited menu.lst. actually, during new kernel installation, user mistakenly select keep old kernel setup instead of install new one. so, follow SoldierBoy instruction and you should be fine:)

---

### Post by Theo148 on 2008-06-01
Well manually changing menu.lst worked, and the new kernel boots fine, so I guess I can call this solved. I'll see about filing a bug report for update-grub though.

I have a hunch that this has something to do with menu.lst files that have been manually edited prior to running update-grub.

---

