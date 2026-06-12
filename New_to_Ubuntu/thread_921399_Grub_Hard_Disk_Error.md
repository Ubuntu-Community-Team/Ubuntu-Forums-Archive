---
title: "Grub Hard Disk Error"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Hedgefox on 2008-09-16
Dear All,

I have a Mac Pro which used to boot with MacOS X or Windows Vista without any problem until the below event.

I used a liveCD and installed Ubuntu 8 on an external HD. Everything went well until I was requested to boot my mac.

I got Grub Hard Disk Error and I have no other way than rebooting on either MacOS X or the liveCD. I cannot boot with Windows Vista on the internal HD or with Ubuntu on the external HD.

I then booted with the liveCD and typed the following steps that I got from some forums:

- mkdir /mnt/racine (nothing to say)
- sudo mount -t ext3 /dev/sdb /mnt/racine (nothing to say)
- sudo gedit /boot/grub/menu.lst (empty file)

Since then, I am stucked.

Please, help me to either successfully install ubuntu or better still get back to my original MacOS-Windows Vista dual boot.

In advance, thank you very much for your attention and help,

Hedgefox

---

### Post by Orange_and_Green on 2008-09-16
> 
- mkdir /mnt/racine (nothing to say)
- sudo mount -t ext3 /dev/sdb /mnt/racine (nothing to say)
- sudo gedit /boot/grub/menu.lst (empty file)


Aren't you missing a
```
cd /mnt/racine
```
or a
```
sudo chroot /mnt/racine
```
between the second and the third step?

If you use ```
cd /mnt/racine
```,
the third step needs to be typed in without the first slash, i.e.
```
- sudo gedit boot/grub/menu.lst
```

Could you please post the contents of this file?
Thanks, bonne chance (good luck):KS

---

### Post by Elfy on 2008-09-16
To see the installed boot

```
cat /mnt/racine/boot/grub/menu.lst
```

Could you also post

```
sudo fdisk -l
sudo blkid
```

---

### Post by dayanandasaraswati on 2008-09-16
If you dont want Ubuntu, you can restore vista's mbr. Just google up how to restore vista's mbr and you'll find millions of entries matching your query. Secondly if you still want ubuntu, make sure that your BIOS is able to boot up through external harddisk. I think since because you are unable to boot through external hdd, your grub is saying error. Check this first. You can browse through bios and find if it has an option of making boot through USB. Latest bios provide this option. But if your bios to too old, you may not have this option. I think upgrading your bios may help you. 

If you are able to still boot through your external hard disk, I recommend you to use Super Grub. You can burn it on a cd and insert the disk when your machine boots. You'll get the super grub menu which will have the list of Operating systems installled and allow you to boot into any one of them(similar to what grub does, but this one loads from a CD). This might be of help to you. Once you boot into ubuntu, you can reinstall grub and try again. If nothing works, your system can permanently use SuperGrub to boot!!!! Super grub can even restore your grub back to your mbr.

---

