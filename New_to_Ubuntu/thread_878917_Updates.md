---
title: "Updates"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Reddoug on 2008-08-03
Hi All

I have a question about updates. I have Unbuntu loaded on a computer that is dual boot with XP. Everytime there is an update, the list of Unbuntu keeps getting longer on the screen were I have to choose between Unbuntu or Windows. Is there away to remove the earlier updates?

Thanks, Doug

---

### Post by bobnutfield on 2008-08-03
I believe you are talking about the list of kernels in the Grub boot screen.  You can delete the older kernels with:

> sudo apt-get -r <kernel-to-remove>

Then, open your /boot/grub/menu.lst file with:

> sudo gedit /boot/grub/menu.lst

and delete the entries for the kernels you have removed.  Be careful with this.  Only delete the kernels you no longer need.  You should keep at least two kernels available to you:  the latest you are using and the immediately previous kernel.

---

### Post by Xiong Chiamiov on 2008-08-03
First, it's Ubuntu, not Unbuntu.  We're not un-buntu-ing anything ;) .

If you want to remove them manually, you can take them out of your grub menu, which is located at /boot/grub/menu.lst.

```

gksudo gedit /boot/grub/menu.lst

```
This will launch gedit as root so that you can change things.  The boot options are down near the bottom.

There is also an option to prevent those from being added, but I"ll have to look it up.

EDIT:
Ah, there it is.  Take a look for this line:
```

# howmany=all

```
and change 'all' to whatever number you would like.

---

### Post by CatKiller on 2008-08-03
Removing the old kernels with Synaptic should also remove the entries from the GRUB menu.lst. But if you fancy editing the file, use either ```
gksudo gedit /boot/grub/menu.lst
``` or ```
sudo nano /boot/grub/menu.lst
``` (see [this page]("http://www.psychocats.net/ubuntu/graphicalsudo") for details) and find the Automagic Kernels section. In that section, find the line that starts **# howmany=**. This line controls how many lines there should be in GRUB's boot-up menu.

EDIT: That's what I get for eating toast at the same time; too slow :)

---

### Post by BGFG on 2008-08-03
If your'e looking for something graphical to edit the grub file you could use QGRUB Editor. If you are sure that you don't want the older kernels, you can remove them via synaptic. I'd advise leaving the two most recent ones on.

You can refer to this:

[http://ubuntuforums.org/showthread.php?t=852807](http://ubuntuforums.org/showthread.php?t=852807)

---

### Post by Reddoug on 2008-08-03
Thanks for the quick replies. Will give them a try and see what I can make work and let you know how it turns out.

Thanks again, Doug

---

### Post by Reddoug on 2008-08-03
Hi

I am not sure what to remove.With this command; gksudo gedit /boot/grub/menu.lst   shows alot that I am not sure what to remove. And with this command;   # howmany=all  would remove everything. If I put 4 would it remove four sections or four lines of code? 

Here is what I have;
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4bd19027-a8dc-48e2-a3a4-a3f78f9e82ff ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4bd19027-a8dc-48e2-a3a4-a3f78f9e82ff ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4bd19027-a8dc-48e2-a3a4-a3f78f9e82ff ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4bd19027-a8dc-48e2-a3a4-a3f78f9e82ff ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4bd19027-a8dc-48e2-a3a4-a3f78f9e82ff ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4bd19027-a8dc-48e2-a3a4-a3f78f9e82ff ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Thanks,  Doug

---

### Post by CatKiller on 2008-08-03
> **Reddoug said:**
> And with this command;   # howmany=all  would remove everything. If I put 4 would it remove four sections or four lines of code? 

No, the howmany is how many get left in :)

howmany=4 would show the latest four kernels in the boot up menu (normal and recovery mode).

Personally, I would remove the 2.6.24-16 kernel in Synaptic, and probably 2.6.24-18 too, since the latest kernel is working for you.

I'd leave editing menu.lst till after.

---

### Post by mcduck on 2008-08-04
Actually I wouldn't recommend editing the boot menu to get rid of the extra kerneöl entries. That would of course make the list shorter, but you'd still have the old kernel versions and all related files wasting your disk space. And with the entries removed from the boot menu, it would be rather hard to ever use them..

You should just uninstall the old kernels. The menu entries will be removed automatically, and you also gain some free disk space. Just open Synaptic, search for "linux" in the package name (for example) to find the kernel packages (linux-image, headers and restricted modules), select all except the latest versions and mark for complete removal.

It's recommended to keep the old kernel for a while after the update, and many people prefer keeping at least 2 kernels all the time. I've found that to be rather useless, I keep the old kernel for couple of days, as long as it takes to confirm that the new one works corectly, and then I uninstall the old one.

---

### Post by JoshuaRL on 2008-08-04
> **mcduck said:**
> Actually I wouldn't recommend editing the boot menu to get rid of the extra kerneöl entries. That would of course make the list shorter, but you'd still have the old kernel versions and all related files wasting your disk space. And with the entries removed from the boot menu, it would be rather hard to ever use them..

You should just uninstall the old kernels. The menu entries will be removed automatically, and you also gain some free disk space. Just open Synaptic, search for "linux" in the package name (for example) to find the kernel packages (linux-image, headers and restricted modules), select all except the latest versions and mark for complete removal.

It's recommended to keep the old kernel for a while after the update, and many people prefer keeping at least 2 kernels all the time. I've found that to be rather useless, I keep the old kernel for couple of days, as long as it takes to confirm that the new one works corectly, and then I uninstall the old one.

I just did a fresh install of Xubuntu so I don't need to delete anything.  But when I search Synaptic like this, I can see all the older kernels there.  If you're looking for them, seach for "linux" and skip down to "linux-generic".  You'll want to keep that one, but from there on down will be what you're looking for.  If you aren't having any kernel issues then just leave the most recent one.

---

### Post by Reddoug on 2008-08-05
Thanks for the help. I used the last suggestion.

Reddoug

---

