---
title: "ftp"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Adaptor on 2008-05-08
hi!  Im using ubuntu server edition 7.10 and am trying to set up a home file server.  i wanted to use proftpd but the only package it will let me use is the vsftpd.  It says it cant find any of the other ones.  Does anyone know why? 

Thanks

---

### Post by Monicker on 2008-05-08
Make sure the Universe repository is enabled in Synaptic, because that is the one which contains proftpd.

---

### Post by Adaptor on 2008-05-08
is there a command for that?

---

### Post by Monicker on 2008-05-08
Open Synaptic, Settings -> Repositories -> Ubuntu Software tab.

---

### Post by Adaptor on 2008-05-08
for the server edition???

---

### Post by Monicker on 2008-05-08
> **Adaptor said:**
> for the server edition???

Edit /etc/apt/sources.list.  I believe there are lines for it there, which can be uncommented. Then do an apt-get update.

---

### Post by Adaptor on 2008-05-08
> **Monicker said:**
> Edit /etc/apt/sources.list.  I believe there are lines for it there, which can be uncommented. Then do an apt-get update.

what happens if i dont have internet conection? the update will not work. Can i still get those packages?

---

### Post by Monicker on 2008-05-08
[http://packages.ubuntu.com/gutsy/i386/proftpd/download]("http://packages.ubuntu.com/gutsy/i386/proftpd/download")


You still have to download it somehow, and transfer it to the server.  Once its there you can use

```
dpkg -i packagename.deb
```

---

### Post by HermanAB on 2008-05-08
Well, vsftpd is good, so why not use it?

Cheers,

Herman

---

### Post by Adaptor on 2008-05-08
thankyou very much for the help so far!  I have one last question though.  I have downloaded the file but how do i move copy it from a flash stick or cd to my server

---

### Post by nowshining on 2008-05-08
u'll have to mount it, 

first

sudo mkdir /media/name

change name to whatever u want

then 

sudo mount /dev/sdb1 /media/name

change name to whatever u put in media and change /dev/sdb1 to where/what the OS mounts for the device..

This can usually be found is /etc/fstab

Anyway, U could of just installed/set-up apache and didn't put any index.htm file in /var/www/ and just put symlinks or so to the shared files :)

---

### Post by Monicker on 2008-05-08
> **Adaptor said:**
> thankyou very much for the help so far!  I have one last question though.  I have downloaded the file but how do i move copy it from a flash stick or cd to my server

I dont know if the server edition automatically mounts usb flash drives.  If not, I would do the following.

fdisk -l , to determine the device name for the partition of the flash drive, which in my case is /dev/sdc1

mkdir /mnt/flash

mount /dev/sdc1 /mnt/flash

cp /mnt/flash/file /some/dir

umount /mnt/flash

---

### Post by sam_delta on 2008-05-08
nvm,, explained above!!

---

