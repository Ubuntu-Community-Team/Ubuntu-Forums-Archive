---
title: "[SOLVED] diskmounter"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Higatron on 2008-09-14
Using some googling, I found the program diskmounter, which I could use to auto mount my second hard drive. The problem is that it's an NTFS hard drive, which is automatically mounted to read only. Is there a way to change this to make it writable? if not, how do I disable diskmounter?

---

### Post by k33bz on 2008-09-14
In the synaptic manager there is a program called "ntfs-config" You could use this program to read and write your ntfs drives

---

### Post by 1/0 on 2008-09-14
You don't need external programs to mount partitions. All you need to do is either add the partition/drive in /etc/fstab (*man fstab* for info) or use a gui equivalent such as gparted.

Install ntfs-config for read/write support.

---

### Post by Higatron on 2008-09-14
Followed 1/0's advice, didn't work the way I thought it would, it renamed my third hard drive (the one I use for xp) and then when it was all done, I could write on the hard drive I wanted to. So it works fine. Thanks.

---

### Post by Bucky Ball on 2008-09-14
Cool. Don't forget to mark the thread as solved (Thread Tools) so others might come here to explore and hopefully fix their probs. :)

---

### Post by 1/0 on 2008-09-14
> **Higatron said:**
> Followed 1/0's advice, didn't work the way I thought it would, it renamed my third hard drive (the one I use for xp) and then when it was all done, I could write on the hard drive I wanted to. So it works fine. Thanks.

Great! Glad it worked out.

---

