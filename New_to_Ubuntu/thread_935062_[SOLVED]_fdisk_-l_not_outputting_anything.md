---
title: "[SOLVED] fdisk -l not outputting anything?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by gschoppe on 2008-10-01
in Gutsy, I just set up an LVM volume... I typed fdisk -l to get the partition list, and I get no output... pv is also not outputting... why would this happen?

---

### Post by Peter09 on 2008-10-01
Think it should be

```
fdisk -l <your disk>
```

---

### Post by mcduck on 2008-10-01
use "sudo fdisk -l". 

Without sudo, fdisk -l will just list the partitions owned by the current user, to list ecverything you need root privileges.

(And no, "fdisk -l" doesn't take disk or partition names or any other parameters, because it doesn't work with any specific disk/partiton but instead just lists all disks & partitions.)

---

### Post by gschoppe on 2008-10-01
fdisk -l sda

still nothing

---

### Post by gschoppe on 2008-10-01
thanks, thats why I was confused.

---

