---
title: "Where is my USB drive?"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by argvar on 2013-06-23
I'm trying to install tails onto a usb drive using ubuntu, but I cannot locate the path of the usb drive.

I right clicked on the drive and went into properties, but it does not tell me the path.

According to tails install help it says it should be somewhere in /dev, like /dev/sdb or /dev/sdc, but neither can be found.
I see a /dev/usb, but it's not it either.

So, where on Earth in this filesystem does ubuntu keep a link to the usb drive?

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]argvar; Hi !

Take a look in the directory /media/
later versions of 'buntu /media/<username>/
And if you mount the device in the file manager, the path is listed at the top of the file manager's window.
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by argvar on 2013-06-23
> **Bashing-om said:**
> [COLOR=#000000]argvar; Hi !

Take a look in the directory /media/
later versions of 'buntu /media/<username>/
And if you mount the device in the file manager, the path is listed at the top of the file manager's window.
[/COLOR][INDENT=3][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]


/media/<user>/<drivename>
is not usable to me, i need the /dev/<devname> bause I'm trying to burn a iso image to the usb drive.

But I found it by typing "df", and it is located in /dev/sdb1

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]argvar; Hey good deal...

ubuntu, more than one way to get it right !
[/COLOR][INDENT=2][COLOR=#000000]
enjoy

[/COLOR][/INDENT]

---

### Post by Cheesemill on 2013-06-24
For anyone else who comes across this thread the following will list the device ID's of any attached USB drives...
```
sudo ls -l /dev/disk/by-id/*usb*
```

---

