---
title: "How do I unmount"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by edcouch on 2008-11-23
Hello folks, I am trying to use partimage, and it keeps telling me that I have to unmount the drive I want to image.  The drive shows up in my system monitor as: /dev/sda1, so I will have to unmount it then image it to my external usb harddrive which shows up as /dev/sdb1.
I have tried to unmount it using the terminal window but I can't seem to get it done.  Help would be appreciated,
Thanks

---

### Post by SuperSonic4 on 2008-11-23
You can't unmount sda1 because you're using it to run ubuntu. Boot up the live cd and use that instead :)

---

### Post by krtica on 2008-11-23
Did you try

```
$ umount /dev/sda1
```

:confused:

---

### Post by Nepherte on 2008-11-23
If you want to image your / disk, you will have to use the livecd.

---

### Post by Dr Small on 2008-11-23
Unmounting /dev/sda1 would not be a good idea ;)

---

