---
title: "Alternative Desktop for Xubuntu"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by afrodeity on 2008-07-19
Somebody on this forum suggested I use an alternate desktop for Xubuntu, which I have now installed behind Puppy Linux (which is running perfectly BTW) is now in a separate partition. Xubuntu is still freezing in session, but at least it startsup. Fixed the mode by hitting e at startup and editing the kernal.

Was okay until I put it behind Puppy. Now have the problem where grub won't see the partition,or can't mount the kernal. Its on hd3. Have tried editing the menu.ls in boot folder but I must be doing something wrong. What would the correct syntax be for Xubuntu on Hd3?

---

### Post by JagDragon on 2008-07-19
My Xubuntu entry goes like this:
```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=73bdf36f-eee9-4e20-9fb9-baa07dd8fad4 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

```

So if you enter in the correct initrd.img for your system, and fix the (hd0,0) to (hd0,2), it should work perfectly.

If you're new to playing around with menu.lst, save backups regularly, and don't remove entries from the file unless they don't work.

---

### Post by linfidel on 2008-07-19
> **afrodeity said:**
> Somebody on this forum suggested I use an alternate desktop for Xubuntu, which I have now installed behind Puppy Linux (which is running perfectly BTW) is now in a separate partition. Xubuntu is still freezing in session, but at least it startsup. Fixed the mode by hitting e at startup and editing the kernal.

Was okay until I put it behind Puppy. Now have the problem where grub won't see the partition,or can't mount the kernal. Its on hd3. Have tried editing the menu.ls in boot folder but I must be doing something wrong. What would the correct syntax be for Xubuntu on Hd3?Probably, you're editing the wrong menu.lst. Try changing the "Title" line a little, since that can say anything you want.  Like, add an asterisk or something to the beginning of the default.  Then see if the menu you get has that asterisk.

There is probably a menu.lst for both puppy and xubuntu.  You can make grub boot from whichever partition you want, and it's easy once you do it, but a little obscure until you become familiar with grub.

I have become **very** familiar with grub, after having about a half dozen different distros at a time on my system, and updating, moving, and deleting them many times.  So, if you need more info, ask and I'll check back.   or someone else will help.

---

### Post by afrodeity on 2008-07-20
Here is the problem when booting with Xubuntu:

#kernel maps protect is an unknown key (error)
#vm.mmap.min.addr unknown key (error)

#could not load lib modules 2.6.21 fatal

got this fatal a number of times

It means that when I go into a session it freezes up.

How do I implement the IceWM solution? Since I can't get into Xubuntu, session freezes, what do I do?

Will attempt the kernel and init suggestion made above.

---

