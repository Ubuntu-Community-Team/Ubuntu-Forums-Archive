---
title: "HOWTO: Make your flash drive work"
date: 2005-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by majikstreet on 2005-07-25
*****[SIZE=5]IF YOU DON'T USE GNOME[/SIZE]


Hi,
I wrote this howto a while ago on another linux forum.

How to get your usb flash drive to work right.

Edit your /etc/fstab and add this at the bottom:
```

/dev/sda1  /mnt/usb  vfat  defaults,rw,noauto,users,sync  0 0

```
Then what you want to do is type:
```

mkdir /mnt/usb

```

Now when you want to use it, plug it in then type:
```

mount /mnt/usb

```
Then before you unplug it type:
```

umount /mnt/usb

```

And yes, it is really "umount" _not_ unmount!
Edit your /etc/fstab and add this at the bottom:
```

/dev/sda1  /mnt/usb  vfat  defaults,rw,noauto,users,sync  0 0

```
Then what you want to do is type:
```

mkdir /mnt/usb

```

Now when you want to use it, plug it in then type:
```

mount /mnt/usb

```
Then before you unplug it type:
```

umount /mnt/usb

```

And yes, it is really "umount" _not_ unmount!




But if you don't can't get sda1 to work, try using sda or sdaX replacing X with a number.

I put two scripts on my desktop to mount and unmount the drive:
mount:
```

#!/bin/bash
mount /mnt/usb

```
unmount:
```

#!/bin/bash
umount /mnt/usb

```


Now if you want to make it automount so you don't have to mount it each time, I think you can just replace noauto with auto.

majikstreet

---

### Post by stwog on 2005-07-25
Are you not using Gnome? When I insert my USB drive a window pops up with all the files on it... I didn't do anything to make that work either.

---

### Post by majikstreet on 2005-07-25
[QUOTE=stwog]Are you not using Gnome? When I insert my USB drive a window pops up with all the files on it... I didn't do anything to make that work either.[/QUOTE]
 Yeah, I don't use gnome-- this was if you don't use gnome i guess then-- (i've only installed ubuntu without x so far, soon i will have gnome on my main computer)

Sorry for any misconceptions!

---

