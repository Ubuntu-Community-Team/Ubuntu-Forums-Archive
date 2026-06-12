---
title: "usb disk uuid change"
date: 2011-04-17
forum: Programming Talk
---

### Post by Bouki on 2011-04-17
Hello there
I want know my usb disk uuid and then change it.
How can I do this ?
help me please.

---

### Post by mikewhatever on 2011-04-17
You can use **tune2fs for both:**

To find out the current UUID
```
sudo tune2fs -l /dev/sdXY | grep UUID
```

for example, in my case
```
$ sudo tune2fs -l /dev/sda2 | grep UUID
Filesystem UUID:          41d737a7-b449-4b4e-a6de-d9c1d096e31a
```

...and to change the UUID
```
sudo tune2fs -U [UUID] /dev/sdXY
```

see **man tune2fs** for more info.

---

### Post by Bouki on 2011-04-17
Thanks a lot man.
but

when i use this command 
sudo tune2fs -l /media/disk | greb uuid
this error happen:
couldnt find the valid filesystem superblock.
where is the problem?
and how can fix it?

---

### Post by BkkBonanza on 2011-04-17
tune2fs is for ext filesystem devices not a mounted directory. You need to give it /dev/sd.. something.

Try typing, **mount** to see a list of what devices are mounted where.

---

### Post by Bouki on 2011-04-17
i used this command:
dev/sd mount
but no such file or directory funded!
i think my usb disk format is not valid.
its my first time using linux .
please help.

---

### Post by BkkBonanza on 2011-04-17
You need to first do,

mount

by itself, this will list current mounts. Then in that list find which device is mounted on /media/disk.

It will look like this, eg.

...other stuff...
/dev/sdc1 on /media/disk type vfat ... etc...
...

Once you see which device, here /dev/sdc1 then you can use the tune2fs command, eg.

sudo tune2fs -l /dev/sdc1 | grep UUID

Make sure you use the actual /dev/sd.. that you see on yours. You must get all the details right or you will get error messages.

---

### Post by mikewhatever on 2011-04-17
Bouki, check out the output of **sudo blkid**. That should show all the partitions with their UUIDs.

---

### Post by Bouki on 2011-04-17
Thanks a lot guys.
where is the problem?
dear BKK
[[IMG]http://www.forumimagecodes.com/images/6uct0z0tltdja0iavak_thumb.png[/IMG]]("http://www.forumimagecodes.com/viewer.php?file=6uct0z0tltdja0iavak.png")
dear mike:
[[IMG]http://www.forumimagecodes.com/images/8hj2un4i2n53s5d2jnif_thumb.png[/IMG]]("http://www.forumimagecodes.com/viewer.php?file=8hj2un4i2n53s5d2jnif.png")

---

### Post by mikewhatever on 2011-04-17
/dev/sdb1 is probably the partition on the usb disk. May I ask why you want to change its UUID?

---

### Post by Bouki on 2011-04-17
is this necessary?
i want use the uuid for my new softeware license.
i captured the screens  and uploaded in [http://www.forumimagecodes.com/](http://www.forumimagecodes.com/) but now its not working!!!!!!

---

### Post by mikewhatever on 2011-04-18
Still not sure why you want that fat32 filesystem UUID changed, but, anyway, tune2fs is obviously not the tool.
Try this howto instead: [http://ubuntuforums.org/showthread.php?t=1240146](http://ubuntuforums.org/showthread.php?t=1240146)

---

### Post by Bouki on 2011-04-18
thanks again.
i red that guide.
it work. but i need hexeditor.
how can find it?

---

