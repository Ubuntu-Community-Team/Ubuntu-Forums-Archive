---
title: "Can ownership be assigned to a Flash-Device upon Format to Ext3/4?"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-05-11
Recently, I purchased a 32 Gib flash card, which was assigned the default file system of fat32.   Upon reformat to a Linux file system (ext4), the device was assigned to root as owner.   

I've since changed ownership via chown commands, BUT, to save time and for simplicity, is there a way using a tool such as gparted, to accomplish both a format and assign a specific user to the device concurrently?

---

### Post by ajgreeny on 2014-05-11
> **JeQhdMD said:**
> Recently, I purchased a 32 Gib flash card, which was assigned the default file system of fat32.   Upon reformat to a Linux file system (ext4), the device was assigned to root as owner.   

I've since changed ownership via chown commands, BUT, to save time and for simplicity, is there a way using a tool such as gparted, to accomplish both a format and assign a specific user to the device concurrently?

Not as far as I am aware. You can do a lot of things with gparted but not something like that.
But, of course, I might be wrong and just out of date regarding gparted uses!

---

