---
title: "[SOLVED] Only command mode after Upgrade to 8.10"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-11-22
I have been working so far trying to install ubuntu to a Lenovo Ideapad Y530 and this is what I have found.

The centrino tecnology came out to the market on July '08,
the Intel wireless 5000 series did on august '08, so the LTS is "obsolete" for this machine. I did an upgrade to 8.10 after all the proper updates and everythig went smoothly until I restarted as I was prompted when the upgrade ended, now when it boots back it stays in command prompt line...
> Starting up...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t (/dev/disk/by=uuid/f5fd7f32-2cde-4ab5-af75-f2f6f7767dc2)=dev (8,6)
kinit: trying to resume from /dev/disk/by=uuid/f5fd7f32-2cde-4ab5-af75-f2f6f7767dc2
kinit: No resume image, doing normal boot...

Ubuntu 8.10 user-laptop tty1
user@user-laptop login:


Any ideas??? Please help!!!!

---

### Post by taurus on 2008-11-22
Log in with your username and password.  Then see what happens if you try to start X server?

```
startx
```

---

### Post by hyper_ch on 2008-11-22
from what I can see above, it shouldn't be
```

by=uuid
```
but
```

by-uuid

```

---

### Post by arashiko28 on 2008-11-22
> **hyper_ch said:**
> from what I can see above, it shouldn't be
```

by=uuid
```
but
```

by-uuid

```

You're right, it was a tipo

---

### Post by arashiko28 on 2008-11-22
I tried the startx
it gave a mile long message all i remember is seeing something about VESA not working and screen detected but no configuration available.

At the end it said fatal error...

Will I have to do a clean installation?

---

### Post by taurus on 2008-11-22
What if you run

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by arashiko28 on 2008-11-22
Thanks for you help, but i fixed it by choosing recovery mode and at the menu that shows, dpkg, where it fixed and upgraded a few broken packages, after that, it just booted alright.:lolflag:

---

