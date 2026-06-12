---
title: "crawling slowly, &quot;need more disc space&quot;"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by gychang on 2008-11-25
on Intrepid, it is suddenly gotten very slow, and some icons the program fails to start.  I get warning "more disc space is needed".  

Is this same as "swap file"?, how do I increase so the programs run smoothly?

gychang

---

### Post by diablo75 on 2008-11-25
Is this a Wubi installation?

---

### Post by gychang on 2008-11-25
> **diablo75 said:**
> Is this a Wubi installation?

it is a Wubi install.

gychang

---

### Post by diablo75 on 2008-11-25
I'm going to bet that your primary partition is FAT32.  I've seen this mess before.  I don't know what the exact cause of the problem is, but I would suspect it's FAT32's max filesize limitation.

There are two things you can do:

1.  Remove Ubuntu with the Control Panel>Add/Remove Programs applet in Windows, and then install Ubuntu by booting from an Ubuntu installation CD, so it can resize your FAT32 partition and insert a new ext3 and swap partition for a clean, native Ubuntu installation.

2.  Convert your FAT32 partition into NTFS.  This might break your Wubi install, but it shouldn't harm windows.  It's very easy to do, but can take hours of waiting.  Here's how:

[http://www.aumha.org/win5/a/ntfscvt.php](http://www.aumha.org/win5/a/ntfscvt.php)

---

### Post by gychang on 2008-11-25
> **diablo75 said:**
> I'm going to bet that your primary partition is FAT32.  I've seen this mess before.  I don't know what the exact cause of the problem is, but I would suspect it's FAT32's max filesize limitation.




Actually it is NTFS and not FAT32.  I will perform your 10 steps as soon as I can get this to run little faster, great steps!

gychang

---

