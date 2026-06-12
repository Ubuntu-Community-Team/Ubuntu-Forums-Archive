---
title: "Wiping MBR"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by Homeground on 2012-04-16
What is the procedure for wiping a mbr completely? I can use the dd if=/sda/zero method and wipe the whole disk, but that seems like using a hammer to crack a nut. Is there something that just wipes the mbr?

---

### Post by mcduck on 2012-04-16
Just tell dd to only write the first 512 bytes:

```
dd if=/dev/zero of=/dev/sda bs=512 count=1
```

...or if you want to keep the partition table, this should work:
```
dd if=/dev/zero of=/dev/sda bs=440 count=1
```

---

### Post by Homeground on 2012-04-16
> **mcduck said:**
> Just tell dd to only write the first 512 bytes:

```
dd if=/dev/zero of=/dev/sda bs=512 count=1
```...or if you want to keep the partition table, this should work:
```
dd if=/dev/zero of=/dev/sda bs=440 count=1
```

Thanks a lot for both of those. Very useful.

---

