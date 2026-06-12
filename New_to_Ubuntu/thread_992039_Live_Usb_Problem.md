---
title: "Live Usb Problem"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by ChrisB111 on 2008-11-24
I built a Ubuntu live cd and using the usb creator inside it I created a live usb stick. I then booted up the stick and check it worked, I didn't change anything. I then booted up windows and using tool I found on this website I created a image of the drive. I then shut down windows and booted up the stick. The loading screen came up and then this.

```
Loading, please wait...

BusyBox v1.10.2(Ubuntu 1:1.10.2- ubuntu6) built in shell (ash)

Enter 'help' for a list of built in commands.

(initramfs)
```

This is probably something simple but I have just started with ubuntu so I don't understand much. Why is it doing this and what does it mean?

Thanks,

Chris

---

### Post by mahiyar on 2008-11-24
Recently I went through the same "booting' pangs. Making live USB from the live CD did not work for me, in my case it stopped at the boot screen saying linux image not found. By chance are you sure you did boot into USB and not into the live CD again? Actually I used this site to make my live disk [http://www.debuntu.org/book/export/html/160](http://www.debuntu.org/book/export/html/160) , a bit complicated but it works.

---

### Post by ChrisB111 on 2008-11-24
Yes I tried twice I definitely booted it off the USB Stick. What I cant get is why taking a image of it change something because that's the only thing I did.

---

### Post by mahiyar on 2008-11-24
I guess image or ISO are made off CD's that is where they have their exact structure in tracks/sectors etc. I suggest remake the USB again. Lesson learnt.

---

### Post by Keen101 on 2008-11-24
I had that message once with a Live-CD. I think it was becuase the cd image was corrupt somehow when i burned it.

try this, it works great for me. You have to install it while running a live-cd though.

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)

---

### Post by C.S.Cameron on 2008-11-24
If you are looking to clone your bootable flash drive, using dd works, when booting from the Live CD with both sticks plugged in:

In terminal
dd if=/dev/hda of=/dev/hdb

Before proceeding confirm that sda is the disk you wish to clone from and sdb is the disk you wish to clone to.

The new flash drive will be bootable if the old one is.

---

