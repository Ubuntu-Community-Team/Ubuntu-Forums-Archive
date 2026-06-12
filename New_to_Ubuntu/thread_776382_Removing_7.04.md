---
title: "Removing 7.04"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by has3o on 2008-04-30
Well upon the boot screen it still has 7.04 how can i remove that becuase im having problems in the hardrive partitioning manager im using the new 8.04 but i cant figure out which one i need to resize to have more harddrive room on the 8.04.

---

### Post by cubeist on 2008-04-30
> **has3o said:**
> Well upon the boot screen it still has 7.04 how can i remove that becuase im having problems in the hardrive partitioning manager im using the new 8.04 but i cant figure out which one i need to resize to have more harddrive room on the 8.04.

Are you sure you are correctly booting into hardy?
In your system monitor, under the first tab it will show your current system and kernel.

If you want to remove old kernels there are two methods, one is permanent and one is not.
For non permanent you could edit your /boot/grub/menu.lst and delete the 7.04 boot option.  (Don't forget to backup your menu.lst before making changes to it!)
The permanent route is to open synaptic, search for the old kernel and choose to uninstall/remove

---

### Post by bilal.17 on 2008-04-30
to delete an entry in grub, remove the part with the entry we want to delete

```
sudo gedit /boot/grub/menu.lst
```

If you want, back it up first just in case you mess something up.

---

