---
title: "Force hard drive to be a certain device"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by deearar on 2008-11-04
Don't know if that subject is worded correctly.

My problem is that my ubuntu file server mixes up devices on every reboot and I was wondering if there was a way to force the boot drive to stay /dev/sda.

A little background. I have a drive with ubuntu on it. I also have a few drives that are used as data drives. Usually, the system boots and...

sda = ubuntu drive
sdb = music drive
sdc = video drive

However, sometimes I reboot and it boots off the ubuntu drive however all the drives get reassigned:

sda = music drive
sdb = video drive
sdc = ubuntu drive

This of course messes up my sharepoints. I look on sdb for music, and it's videos instead. Is there any way to force a certain drive to always be assigned to the same position so I don't run into this problem?

---

### Post by taurus on 2008-11-04
Did you use UUID to mount those drives or did you use the generic name like /dev/sda1 to mount them?

What does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by deearar on 2008-11-04
I just used Generic names to mount them, like this:

/dev/sdb1 /mnt/Storage1 ext3 defaults 0 0

Is the UUID actually tied to the physical device? If so that sounds like what I need to do!

---

### Post by taurus on 2008-11-04
Yes.  So, why don't you replace the /dev/sdb1 (and others) with the actual UUID.  You can find out what they are running this command from a terminal.

```
ls -la /dev/disk/by-uuid
```

---

### Post by deearar on 2008-11-05
Ok, so before I start making more changes to my fstab, in my example would it change from,

/dev/sdb1 /mnt/Storage1 ext3 defaults 0 0

to:
UUID=83f95f3f-3aa3-493a-8937-406165580a19 /mnt/Storage1 ext3 defaults 0 0

?

---

### Post by taurus on 2008-11-05
That's right, assuming you have the right UUID.

---

