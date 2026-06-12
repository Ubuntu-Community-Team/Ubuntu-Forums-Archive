---
title: "mount"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-07-09
i just mounted my dvdrom to /media/cdrom
and later when i tried to umount it by 
umount /media/cdrom
it says the device is busy could any one help me plz.

---

### Post by iaculallad on 2008-07-09
Try:
```

fuser -km /media/cdrom
```

---

### Post by phanipalagummi on 2008-07-09
sorry not working,by the by what is fuser

---

### Post by iaculallad on 2008-07-09
> **phanipalagummi said:**
> sorry not working,by the by what is fuser

What about:

```
umount -l /media/cdrom
```

For further reading on fuser:

```
man fuser  
```

---

### Post by phanipalagummi on 2008-07-09
thank you it worked
but what is the difeerence between 
umount /media/cdrom and umount -l /media/cdrom.

---

### Post by iaculallad on 2008-07-09
> **phanipalagummi said:**
> thank you it worked
but what is the difeerence between 
umount /media/cdrom and umount -l /media/cdrom.

Try accessing the man page using the terminal for more detailed explanation on umount and the -l switch:

```
man umount
```

---

### Post by ChameleonDave on 2008-07-09
> **phanipalagummi said:**
> i just mounted my dvdrom to /media/cdrom
and later when i tried to umount it by 
umount /media/cdrom
it says the device is busy could any one help me plz.

I suspect that you either have a file manager window open with the media open in it, an application (such as OpenOffice.org) open with a file from the media open in it, or a terminal window with its current directory set as a location on the media.

> **phanipalagummi said:**
> thank you it worked
but what is the difeerence between 
umount /media/cdrom and umount -l /media/cdrom.

You can tell, from its result, that it has a kind of forcing effect.

Simply do "man umount" on the command line for more information.

---

### Post by phanipalagummi on 2008-07-09
thank you guys.:)

---

