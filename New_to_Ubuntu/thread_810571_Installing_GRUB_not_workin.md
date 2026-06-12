---
title: "Installing GRUB not workin"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2008-05-28
I followed these steps after installing XP on a partition for gaming:
started live cd and opened a terminal then typed the following:
sudo grub
grub> find /boot/grub/stage1
 (hd1,1)
root (hd1,1)
setup (hd0)
quit

Then I rebooted and it had no choice of where to boot just auto started going into windows? Please help.

---

### Post by OffAxis on 2008-05-28
I think that should be
setup(hd1)

so 
```
sudo grub
grub> find /boot/grub/stage1
(hd1,1)
root (hd1,1)
**setup (hd1)**
quit
```

or just use the supergrub disc.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by bumanie on 2008-05-28
If you are dual booting off the one drive, which I think you are as you say a partition, rather than a seconday hard drive, it should be 

sudo grub
root (hd0,1)
setup (hd0)
quit

Command (h1,1) would be instructing grub to install to a the second partition of a secondary hard drive.

---

### Post by bsharp on 2008-05-28
Or just do
```
sudo grub-install --root-directory=/boot --recheck
```

---

### Post by OffAxis on 2008-05-28
@ bumanie
That's what I was thinking, too, but if 
find /boot/grub/stage1
came back with (hd1,1)
then it has got to be there, right?

Maybe there's a flash drive or a storage only hard drive attached - I don't know, I can't quite think of what would yield the second partition on the second hard drive as the location for stage1 (maybe there are two drives and they 're reversed in the BIOS boot sequence?)

---

### Post by bodhi.zazen on 2008-05-28
> **OffAxis said:**
> @ bumanie
That's what I was thinking, too, but if 
find /boot/grub/stage1
came back with (hd1,1)
then it has got to be there, right?

Maybe there's a flash drive or a storage only hard drive attached - I don't know, I can't quite think of what would yield the second partition on the second hard drive as the location for stage1 (maybe there are two drives and they 're reversed in the BIOS boot sequence?)

No.

The command "find /boot/grub/stage1" identifies the Ubuntu boot partition (which in this case is the same as / )

To set up a partition, ie install grub, use setup (hd1,1)

But to set up the MBR, use 

setup (hd0)

Since that command did not work, try :

```
setup (hd1)
```

---

