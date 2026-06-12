---
title: "Exclamation in triangle for root partition"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by jesrani on 2008-05-21
I have successfully cloned my 7.10 install to a new computer and upgraded 8.04 from the alternate CD. But I find that in GParted, the root partition (/sda1) has a Triangle and Exclamation in it and does not show mount point. Is this ok?

---

### Post by alexandremrj on 2008-05-21
That is completely normal.

What is means is that it can't read the file system in there because it's is mounted and as such can't perform several operations in there.

Don't worry about it

---

### Post by jesrani on 2008-05-21
> **alexandremrj said:**
> That is completely normal.

What is means is that it can't read the file system in there because it's is mounted and as such can't perform several operations in there.

Don't worry about it

Actually there was a problem in my fstab. I had accidentally removed / option from root partition. It works ok now.

---

