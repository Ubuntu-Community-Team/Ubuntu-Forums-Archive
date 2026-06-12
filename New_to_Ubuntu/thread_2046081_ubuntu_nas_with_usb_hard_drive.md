---
title: "ubuntu nas with usb hard drive"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by joshb1 on 2012-08-22
hello.

i have ubuntu server running as a NAS and space is getting used fast i would like to know how i can add more space using a usb harddrive.

---

### Post by Bashing-om on 2012-08-22
Josh; Hi! Welcome to the forum.

 Firstly, Is this your first time with a server? Have you checked your /var/log *files for any runaway stuff ?
 Secondly on the usb drive ... is that in reference to a present drive ...or future expansion ?

 CUL <==BDQ

---

### Post by lukeiamyourfather on 2012-08-22
The best practice would be to mount the external disk to /mnt/whatever and then share that directory. Or make a symbolic link to that from an existing share.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

