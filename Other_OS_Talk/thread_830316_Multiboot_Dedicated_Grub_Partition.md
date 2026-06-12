---
title: "Multiboot: Dedicated Grub Partition"
date: 2008-06-15
forum: Other OS Talk
---

### Post by Nessa on 2008-06-15
Since we all like to experiment and explore, I was wondering if you guys use a dedicated grub partition for your booting needs. I doing a lil project for myself to put 5 linux distros into an 80GB usb drive. I currently have Mint installed there and will soon add Arch.

So, do you use it? Why? Would you recommend it?

---

### Post by mcurran on 2008-07-11
I have a multiboot system with Vista/OSx86/Linux Mint and I was thinking of setting up a dedicated grub partition as a workaround for the Darwin bootloader only defaulting to the active partition and thus creating the need to make a second selection if booting from the vista bootloader.  My ideal situation would be to have the windows partition active, since it enables the hidden recovery partition option (F9) on startup and also because I don't like GRUB's resolution with the distro I'm using.

So I would only pick once, the OS I want to boot from one menu.  This can be done by using grub and the hide/makeactive options for fooling the darwin loader, but again I want to use windows, so I'm going to have windows point to a grub pointing to grub/linux and windows pointing to a grub pointing to grub/darwin.  That way I can have a grub configured for each and set the default timeout to 0.

What is the smallest linux I could use to create a dedicated grub partition for this, or is there a way to install just a preconfigured grub only (I'm going to try this by building the dedicated grub configuration, saving it, installing it to dedicated partition, reconfiguring and then saving).  Or would it be easier to install grub within windows somehow?

I plan on using EasyBCD.

---

### Post by Endolith on 2009-01-23
If you create a dedicated grub partition, will Ubuntu still update it automatically when new kernels are installed?

I was thinking of making a small FAT partition for files that need to be openable by any OS without any drivers, etc. and thought maybe I could install GRUB there, too.

---

### Post by maybeway36 on 2009-01-23
When I made a 6-OS multiboot computer, I used a small partition to do double-duty as both a GRUB partition and FreeDOS. It's not strictly necessary, though.

For the Ubuntu and Debian entries, instead of using /boot/vmlinuz-2.6.xxx and /boot/initrd.img-2.6-xxx, I used /vmlinuz and /initrd.img -- these are symlinks to the newest kernel and initrd.

---

### Post by estyles on 2009-01-23
> **Endolith said:**
> If you create a dedicated grub partition, will Ubuntu still update it automatically when new kernels are installed?

The point of making a dedicated Grub partition is so that Ubuntu (and other distros) can't and don't touch it.  Instead, each distro maintains its own menu.lst file.

You can create a grub partition easily enough.  Create a new partition (can be ~50MB or so), and copy your /boot/grub directory to that partition from any distro.  You can copy the whole /boot directory if you want to, but I don't believe it accomplishes much.

Then edit the menu.lst so it simply loads the grub stuff off the appropriate partition for the OS you want to boot.  You can either use configfile or chainloader.  (For the examples below, please someone correct me if I've made a mistake, I can't check my own system right now - will fix later if I notice an error...)

For configfile, you want something like:```
Ubuntu 8.10
savedefault
configfile (hd0,5)/boot/grub/menu.lst
```

(I always use savedefault, and set "default saved" higher up in the menu.lst file.)

For chainloader, you want something like:```
Ubuntu 8.10
savedefault
root (hd0,5)
makeactive
chainloader +1
```

For both of the above, you have to substitute (hd0,5) for the block notation for the correct partition.  If it's installed on /dev/sda6, then use (hd0,5), because sda notation is 1-based and block notation is 0-based.

For a Windows partition, you have to use the chainloader method.  For Linux, you have to setup grub on each partition if you want to use the chainloader.

Once you've modified the menu.lst file, open a terminal.  Replace (hd0,1) below with the actual block notation for your grub partition, and (hd0) with the correct device name).```
sudo grub
root (hd0,1)
setup (hd0)
exit (...or it quit?  I forget... try both)
```


If you are trying to use chainloader for a linux partition, you have to also do the following.  Replace (hd0,5) with the correct block notation for the partition.```
sudo grub
root (hd0,5)
setup (hd0,5)
exit
```

I'm nearly certain this is correct for the chainloader method, and it worked fine on my last computer, but for my new computer, only the configfile version works.  Both methods should have the same basic effect, so if one way doesn't work, try the other.

Anyway, when you do that, Ubuntu will manage its own menu.lst file, without hurting your grub partition's menu.lst, which you can keep up manually, because it doesn't have to worry about kernel images or anything.

When you install a new distro, if possible, don't let it install grub to the master boot record.  I know that Arch allows you to specifically install grub to its own partition - which is nice.  Ubuntu always overwrites the mbr (I think you can install it without installing grub, but in that case, you've got to go through some other steps to make it work right...), after which you have to go through the "sudo grub; root (hd0,1); setup (hd0)" trick again... not too difficult, but mildly annoying.

---

### Post by maybeway36 on 2009-01-24
May I recommend:
```
title Ubuntu 8.10
root (hdX,X) <-- change this
kernel /vmlinuz root=/dev/hdxx ro quiet splash <-- change 'root=' part
initrd /initrd.img
```
/vmlinuz and /initrd.img are symlinks to the newest kernel and initrd installed.

---

