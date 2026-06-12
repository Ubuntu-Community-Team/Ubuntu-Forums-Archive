---
title: "USB memory stick becoming read-only for no apparent reason!"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by t0p on 2008-06-21
I've got a 1GB USB flash memory stick.  When I plug it into the computer, it works just fine - I can save and delete files on it as I please. But if I leave it in for a while, I'll discover that it's become read-only.  I'll no longer be able to save or delete anything on the stick.  I have to remount it to make it work again.

Any ideas?

---

### Post by Nikitas350 on 2008-06-21
I had the same problem. Format is to fat32 and it will work (i hope) ;)

---

### Post by john.nicholls on 2008-06-22
If you have a look at the /var/log/syslog it may indicate what is happening to cause this. In my case it happens when I try to write to the memory stick to a non-existent partition or something else that the stick does not like.

---

### Post by Stefanie on 2008-06-22
> **t0p said:**
> I've got a 1GB USB flash memory stick.  When I plug it into the computer, it works just fine - I can save and delete files on it as I please. But if I leave it in for a while, I'll discover that it's become read-only.  I'll no longer be able to save or delete anything on the stick.  I have to remount it to make it work again.

Any ideas?

i had a similar problem with my external hdd. this is what i did:


```
sudo chown -R username:username /media/disk
sudo chmod -R 755 /media/disk

```

of course you have to change "/media/disk" to the path of your usb-stick. plug it in and you'll see the path in nautilus, it will be similar to /media/disk .

---

