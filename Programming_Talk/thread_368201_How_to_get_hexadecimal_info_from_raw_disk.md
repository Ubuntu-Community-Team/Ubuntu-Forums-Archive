---
title: "How to get hexadecimal info from raw disk"
date: 2007-02-23
forum: Programming Talk
---

### Post by I.You on 2007-02-23
Hi there.

I tried like this:

cat /dev/sda2 > test

in order to get superblock info. from HDD.
I'm not sure but it's likely to possible to read by hexadecimal code in emacs.
Is there any other program able to do this?

---

### Post by Lux Perpetua on 2007-02-23
I've used GHex to read/write binary files in hexadecimal. It's in the repositories. For a command line interface, try hexdump.

---

### Post by I.You on 2007-02-23
Thanks a lot, Lux.

It's so simple!
very helpful for me.

Thank you.

---

### Post by phossal on 2007-02-23
GHex is pretty, but I can't remember if it's more or less useful than khexedit. I liked them both, but once I *understood* khexedit, I think I decided that I liked it more.

---

### Post by steve.horsley on 2007-02-25
I don't think you can directly open devices with ghex. I suggest you use dd to copy chunks of the hard disk to file, and then view them. Frinstance, to view your partition table:
[B]dd if=/dev/hda of=mbr bs=512 count=1
ghex2 mbr[/B]

---

