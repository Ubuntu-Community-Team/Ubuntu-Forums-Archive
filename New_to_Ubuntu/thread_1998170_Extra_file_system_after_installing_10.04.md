---
title: "Extra file system after installing 10.04"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by jripple on 2012-06-06
I just installed 10.04 using the option to use the entire drive.  I assumed it would wipe out all pre-existing file systems.  However, after installation finished, there was an extra 166 GB file system with basically nothing in it.

How do I get rid of it?

---

### Post by cortman on 2012-06-06
> **jripple said:**
> I just installed 10.04 using the option to use the entire drive.  I assumed it would wipe out all pre-existing file systems.  However, after installation finished, there was an extra 166 GB file system with basically nothing in it.

How do I get rid of it?

Make sure it is just extra and unnecessary. You can delete the partition and absorb the unallocated space into your Ubuntu partition, assuming they're side-by-side.
Use GParted to delete the partition, but to add the extra space to your Ubuntu partition you will need to boot from a LiveCD.

---

### Post by Gone fishing on 2012-06-06
Its probably just your old ntfs partition, you could delete it reformat to ext4 using partition editor or even keep it as ntfs  and then mount it as say /home/user/storage or even just /storage I'd rather do that than resize your existing partition to make use of the space.

---

