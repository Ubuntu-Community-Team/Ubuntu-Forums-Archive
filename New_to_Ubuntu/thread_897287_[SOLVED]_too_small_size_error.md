---
title: "[SOLVED] too small size error"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by mike22 on 2008-08-22
Hi, I'm getting the too small size error at the partition part of the ubuntu 8.04.1. It says "too small size" I have 7.45 gb of free space left for installation. My HD size is 74 gb.


Plz help thank you.

---

### Post by mcduck on 2008-08-22
Is this after creating the partition for Ubuntu, or while trying to resize an existing Windows partition?

If it's while resizing, the problem could be simply that there isn't enough room to re-arrange the data on the windows partition.

---

### Post by mike22 on 2008-08-22
it's while im resizing. it's step 4 of the installation and im doing a dual boot.

---

### Post by mcduck on 2008-08-22
> **mike22 said:**
> it's while im resizing. it's step 4 of the installation and im doing a dual boot.

Then how big (or small) partition you are trying to create? Either it's too small, or then, like I already suggested, your disk doesn't have enugh space to re-arrange the data on your window spartition, and because of that resizing is impossible. In that case you need to remove some fiels from your Windows partition, or buy another hard disk.

7,4GB should be enough for Ubuntu, but if you are tryin to make the partition much smaller than that it could be a problem.

---

