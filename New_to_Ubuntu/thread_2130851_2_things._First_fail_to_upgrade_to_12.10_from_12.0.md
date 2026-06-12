---
title: "2 things. First fail to upgrade to 12.10 from 12.04, Second making custom scripts..."
date: 2013-03-30
forum: New to Ubuntu
---

### Post by Drew U on 2013-03-30
So the first thing I tried to do an upgrade on my laptop (Asus k52jr) Ubuntu 12.04 64bit, to 12.10 64bit, It failed to do a complete upgrade. so it did a partial. (off of memory I tried a few days ago)

Second can someone post me to information on how to program things for Ubuntu. I want to make a context menu script to automatic run a script to install tar files.

IE: right click tar file, install (runs script to extract to folder. install. delete folder) automatic based on files name and directory, I do have programming knowledge but I need to know what languages Ubuntu uses for such a thing and where I need to install it. I cannot seem to find any info through random Google searches.

---

### Post by schragge on 2013-03-30
Generally speaking, you cannot automate installing programs from sources (IIUC what you mean with* install tar files*). The often cited sequence
```

tar xf program-version.tar.gz
cd program-version
make
sudo make install

``` will only work if all prerequisites are already installed. What those prerequisites are in each particular case is often described in files like INSTALL or README inside tarball.

---

