---
title: "NTFS and Ext3:"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by sandylovesgnr on 2008-09-21
I have ubuntu installed from inside windows option. It dint create a new partition, uses the same partition ntfs.
I want to know, will it access disk files as ext3?, i have to check the latency of indirect blocks, will this system access files as ext3 does?

---

### Post by SunnyRabbiera on 2008-09-21
What?

---

### Post by sandylovesgnr on 2008-09-21
I had windows installed in my machine. I installed ubuntu, but as i dint install it from disk drive, it used the existing partition of NTFS and dint create another one. I want to check if ubuntu will do file access internally as a normal EXT3 does?

---

### Post by sayakb on 2008-09-21
Do you wish to access your ext3 partitions from windows? Download and install the EXT2IFS driver on Windows: [http://fs-driver.org](http://fs-driver.org). This enables read/write access to ext3 partitions from Windows.

EDIT: Just saw the last post. Ubuntu will access all ext3 drives just the same way it does when installed on a separate partitions and not on a virtual one using wubi.

---

### Post by sandylovesgnr on 2008-09-21
No that's not what i want to do. I am accessing files from ubuntu. I have to do an exercise of latency check, while reading files from direct blocks and indirect blocks. But if being intalled in ntfs partition, will it have same internal access scheme as ext3?

---

### Post by sandylovesgnr on 2008-09-21
My system has 2 drives, C: and D:.
 C: drive has windows installed.
 D: drive had some data.

Now both the drives were NTFS. I installed ubuntu from iso from windows. Now ubuntu is installed in D: (NTFS partition only).

When i boot into ubuntu, it says, NTFS filesystem type.

My question is: When ubuntu accesses files, will it read them as ext3 does? i mean internal read operation. My exercise wants me to study latency of direct and indirect block read. I hope u got my point.

---

### Post by Jordanwb on 2008-09-21
He's using Wubi. It won't be the same because they're different file systems and files are placed differently on the partition.

---

