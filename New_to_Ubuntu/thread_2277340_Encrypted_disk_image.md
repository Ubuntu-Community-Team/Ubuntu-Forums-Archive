---
title: "Encrypted disk image"
date: 2015-05-08
forum: New to Ubuntu
---

### Post by hmiersch on 2015-05-08
Hi
Is it possible to create an encrypted disk image that can be mounted (with a password) and then used like a regular HD? The idea is to store sensitive files in that image. When I want to work with those files I mount the image, and when I'm finished I eject the disk to keep the files away from prying eyes. 
I tried something whose name ends in -ehd but that didn't get far. After entering a password I got a "segmentation fault" and the file was unusable. Did I do something wrong?

PS I use 14.04

---

### Post by dino99 on 2015-05-08
Modifying a snapshot is not easy (aka disk-image), the common crypting is done on partition where the files are embedded.
[https://www.digitalocean.com/community/tutorials/how-to-use-dm-crypt-to-create-an-encrypted-volume-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-use-dm-crypt-to-create-an-encrypted-volume-on-an-ubuntu-vps)
[http://thesimplecomputer.info/full-disk-encryption-with-ubuntu](http://thesimplecomputer.info/full-disk-encryption-with-ubuntu)
[http://www.howtogeek.com/195124/how-to-easily-encrypt-files-on-windows-linux-and-mac-os-x/](http://www.howtogeek.com/195124/how-to-easily-encrypt-files-on-windows-linux-and-mac-os-x/)

---

### Post by mcduck on 2015-05-08
You could also take a look at EncFS, while it doesn't work with disc images, it allows you to create encrypted folders (which are then mounted as FUSE filesystem, and the unencrypted version appears like a removable drive would.)

Pretty convenient way of keeping some stuff encrypted and easily accessible without having to encrypt your whole filesystem. And EncFS also works well with cloud storage (Dropbox, Google Drive etc) and there are tools for Windows, OSX and Android as well so it can be accessed from any of them.

I recommend using Gnome EncFS Manager as a nice graphical interface for creating & mounting EncFS systems: [http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html]("http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html")

---

