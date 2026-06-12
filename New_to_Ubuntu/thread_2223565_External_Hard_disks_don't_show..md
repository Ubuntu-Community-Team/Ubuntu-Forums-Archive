---
title: "External Hard disks don't show."
date: 2014-05-11
forum: New to Ubuntu
---

### Post by fotoflex on 2014-05-11
Hi,
I was used to seeing my external HDD's in the bar on the left side of my screen.
Also, they would open a window when I plugged them in.
Now the're gone, I have to use Disk Utility to mount them, and then they only appear in the bar on the left in an opened window.
But at least I can access them.
My MP3-player still does what I described above, it's just the HDD's that don't.
I first noticed it when I started the laptop up, a couple of days ago.
I don't remember changing any settings.

---

### Post by jmeeter on 2014-05-11
How is it formated? NTFS, ext3, ext4

If its a USB drive try the following command in a terminal

```
lsusb
```

this should list all your usb devices. Post the output here.

---

