---
title: "[SOLVED] Help ! Only 640x480 Screen Resolution Available..!!?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-14
Hi,

After installing/uninstalling a new kernel/Envy.

I have only 640x480 as the highest resolution to choose from...

How to fix?

Thanks..

---

### Post by ChameleonDave on 2008-06-14
> **hopelessone said:**
> Hi,

After installing/uninstalling a new kernel/Envy.

I have only 640x480 as the highest resolution to choose from...

How to fix?

Thanks..

Yes, I too had the problem of a new kernel installation ruining my video configuration.  I found that only by removing all extraneous kernels and reinstalling the 2.6.24-19 version of everything could I get things working again.  I also ran EnvyNG again.

---

### Post by hopelessone on 2008-06-14
Did all that rebooted and only 640x480 available as highest resolution..!!

Any other way to get back to 1680x1050?

Thanks

---

### Post by hopelessone on 2008-06-14
Added Screen shot..

---

### Post by hopelessone on 2008-06-14
Phew!
```
sudo dpkg-reconfigure xserver-xorg
```

Reset them...

Gotta remember that one!!

---

### Post by ChameleonDave on 2008-06-14
Perhaps you could post the output of this:

```

ls /boot/
cat /etc/X11/xorg.conf

```

---

