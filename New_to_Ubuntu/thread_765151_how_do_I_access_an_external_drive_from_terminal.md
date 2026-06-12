---
title: "how do I access an external drive from terminal"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by ben22 on 2008-04-24
Hi,

I want to copy files from the external drive to the pc. since there are some permissions problems I want to do this with sudo.

With which commands can I find the external drive?

root@ben-desktop:/# ls
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old


Thx,
Ben

---

### Post by DezSP on 2008-04-24
If you type **sudo nautilus &** it'll give you a root file manager, might make life easier.

Usually Ubutnu will mount drives as /media/disk-X/, if it doesn't exist, then post back here and someone will help you mount it. :)

---

### Post by billgoldberg on 2008-04-24
> **ben22 said:**
> Hi,

I want to copy files from the external drive to the pc. since there are some permissions problems I want to do this with sudo.

With which commands can I find the external drive?

root@ben-desktop:/# ls
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old


Thx,
Ben

The easiest way would be to open nautilus as root, that should take care of any permission problems.

```
gksudo nautilus
```

If you want to only use the terminal, I believe it's located in /media/name of harddrive.

There is a command "cheat sheet" [here]("http://linuxowns.wordpress.com/2008/04/23/hardy-cheat-sheet/") that might come in handy for the future.

---

### Post by Ub1476 on 2008-04-24
```
cd /media
dir
cd *name of external hdd here*
cd to whatsoever directory
sudo cp *name of file* ~/*name of folder in home directory to copy to*
```

If you want to copy a lot of documents file (.doc for instance) you can write:

```
sudo cp .doc*
```

To copy a directory:

```
sudo cp -dir *name of dir*
```

---

