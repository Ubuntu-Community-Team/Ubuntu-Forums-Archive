---
title: "getting out of windows"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by liangongkid2 on 2012-05-17
Hi guys
       This is the first time I have used the forum,so if I do anything I shouldnt I apologise.
       I am running ubuntu 12.04 within windows vista and I want to go with ubuntu for all my computing.How do I get out of windows without harming my ubuntu setup.
                                  Best regards .

---

### Post by brenden1030 on 2012-05-17
If it's running inside a VM it is not possible to "move" it you would have to do a fresh install  by booting a CD.

---

### Post by Vereinfachen on 2012-05-17
It is possible to move out of the VM, but it's complicated.

liangongkid2, trust me, this will only make problems. The easiest way to ditch Windows will be to backup your important files somewhere and then reinstall Ubuntu to the whole drive.

---

### Post by Frogs Hair on 2012-05-17
If Wubi was used to install you will have to move Ubuntu to a partition and reformat the Windows Partition.

This is a lot work and it is much easier to backup the Ubuntu files download a 12.04 ISO and use as much of the disk as you want during the installation.

The disk will be re-formated during the installation

---

### Post by choppyfireballs on 2012-05-17
> **Vereinfachen said:**
> It is possible to move out of the VM, but it's complicated.

liangongkid2, trust me, this will only make problems. The easiest way to ditch Windows will be to backup your important files somewhere and then reinstall Ubuntu to the whole drive.

This is correct this is what I would recommend however if you REALLY want to move ubuntu I recommend backing up folders in your current setup then just reinstaling them or copying them into your new install.

---

### Post by forrestcupp on 2012-05-17
If you installed Ubuntu with Wubi, and you really want to migrate it to its own partition instead of being run in Wubi, [here is how you do that](https://help.ubuntu.com/community/MigrateWubi). Make sure to back up your files first, just in case something happens.

I'm with everyone else who thinks that you should just do a clean install and restore your backed up files. But if you really want to do it that way, that's how you do it.

---

