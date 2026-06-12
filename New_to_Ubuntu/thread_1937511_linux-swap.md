---
title: "linux-swap"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by maheshtatva on 2012-03-08
i found linux-swap on my extended partitoin does it required or else i will change this to ntfs

---

### Post by acimi66 on 2012-03-08
It is recommended to have a swap partition about the size of the amount of RAM you have on your computer i.e.2 gb  of RAM swap would be 2gb - It has to do with helping the RAM (memory allocation) when you are pushing your computers RAM.

At least I think thats what it's for. But you should keep it.

---

### Post by lisati on 2012-03-08
The swap partition is used when linux needs to free up some RAM. It is also useful for suspend and hibernate modes. If you decide to keep swap turned on, think carefully before reformatting it to NTFS.

For more information, see [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) and [http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

---

### Post by ixtok on 2012-03-08
> **maheshtatva said:**
> i found linux-swap on my extended partitoin does it required or else i will change this to ntfs

Keep the swap file.

---

