---
title: "Formatting a HDD"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by `Jon on 2008-08-18
I've been trying to format two drives in Ubuntu with no success. 

If I type df -h in terminal, it shows me the two drives I want to format,

/dev/hdd1             150G   70M  149G   1% /media/disk
/dev/hdc1             150G   70M  149G   1% /media/disk-1


But if I type fdisk /dev/hdd1, I get the error "Unable to open /dev/hdd1"

I've even tried formatting the drives in DOS, but I still don't have the permissions to write to the drive in Linux. If I use sudo nautilus, I can't see the two drives.

I know they're not faulty because until a couple of days ago both drives were full.

How can I solve this problem?

Thanks!

---

### Post by nicedude on 2008-08-18
Use the graphical partition editor as it is allot easier to use. System -> Administration -> Partition Editor

Just make sure you know what you want to do :-)

---

### Post by `Jon on 2008-08-18
I don't know if it's because of the version of Ubuntu I have, but I don't have that option. I'm using Feisty 7.04.

---

### Post by Yuki_Nagato on 2008-08-18
If you cannot see the drives in nautilus, are they mounted correctly?

```
sudo mkdir /media/XXX
mount /dev/hdd1 /media/XXX
```

---

### Post by `Jon on 2008-08-18
mount: according to mtab, /dev/hdd1 is mounted on /media/disk

I can see the drives in a normal file browser, I just can't edit them.

---

### Post by nhasian on 2008-08-19
Yeah i didnt have it either by default in Hardy 8.04 but you can easily add it by going to add/remove software and searching for gpart
you should find "Gnome partition Editor"

> **`Jon said:**
> I don't know if it's because of the version of Ubuntu I have, but I don't have that option. I'm using Feisty 7.04.

---

### Post by mcduck on 2008-08-19
You should unmount the partitions before you try to edit them..

---

