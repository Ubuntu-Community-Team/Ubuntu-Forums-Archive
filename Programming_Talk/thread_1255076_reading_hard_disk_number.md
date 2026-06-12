---
title: "reading hard disk number"
date: 2009-09-01
forum: Programming Talk
---

### Post by veda87 on 2009-09-01
Can anyone tell me how to read the Hard Disk Serial Number as well as the volume number....

---

### Post by unutbu on 2009-09-01
```
udevadm info -a -p /sys/block/sdb | grep serial
```
yields ```


    ATTRS{serial}=="**2GEVLJDW**"
    ATTRS{serial}=="0000:00:1a.7"

```
thus showing the serial number of the second hard drive, /dev/sdb.

You can also find this information by parsing the output of 
```
sudo lshw -C disk
```

I don't know what you mean by volume number.

---

### Post by soltanis on 2009-09-01
Maybe he means the logical volume number, if he's using LVM. Unfortunately I don't know how to get this.

---

### Post by veda87 on 2009-09-05
> **unutbu said:**
> ```
udevadm info -a -p /sys/block/sdb | grep serial
```
yields ```


    ATTRS{serial}=="**2GEVLJDW**"
    ATTRS{serial}=="0000:00:1a.7"

```
thus showing the serial number of the second hard drive, /dev/sdb.

You can also find this information by parsing the output of 
```
sudo lshw -C disk
```

I don't know what you mean by volume number.

Thanks... This command was helpful....

Now, I am planning to write a C program to read the hard disk serial number. I dont have any idea of from where to start with.

Can anyone help me on this...

---

