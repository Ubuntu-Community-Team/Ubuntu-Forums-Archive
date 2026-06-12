---
title: "Moving or extracting tar.gz to USB flash (/dev/sdc)"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by Kneegrowplease on 2012-04-22
I'm having problems moving or extracting this file to a sd card in a usb flash drive. tried this:


```
knee@knee-ET1330:~/Downloads$ sudo -xvf debian_chroot.tgz > /dev/sdc
bash: /dev/sdc: Permission denied

```

tried it without sudo.


tried this:


```
knee@knee-ET1330:~/Downloads$ sudo mv debian_chroot.tgz > /dev/sdc
bash: /dev/sdc: Permission denied

```


my commands must be halfway right or I think I'd get a different more "phuckoffy" output...

---

### Post by papibe on 2012-04-22
Hi Kneegrowplease.

You may destroy the USB file system if you redirect the out to the device itself. Instead extract the files into the directory the USB is being mounted.

Take a look at this tar [tutorial]("http://www.thegeekstuff.com/2010/04/unix-tar-command-examples/") for several tips.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by jerome1232 on 2012-04-22
you don't write files directly to the block device!

You need to copy the file to the mount point (should auto mount to somewhere in /media), if it's unmounted than you need to mount it then copy it.

an easy way to see where it's mounted at is the below command.

```
mount | grep /dev/sdc
```


if that returns nothing than you need to mount it.


```
sudo mount /dev/sdc1 /mnt
tar xvfz debian_chroot.tgz -C /mnt
sudo umount /mnt

```

---

### Post by Kneegrowplease on 2012-04-22
> **jerome1232 said:**
> you don't write files directly to the block device!

You need to copy the file to the mount point (should auto mount to somewhere in /media), if it's unmounted than you need to mount it then copy it.

an easy way to see where it's mounted at is the below command.

```
mount | grep /dev/sdc
```


if that returns nothing than you need to mount it.


```
sudo mount /dev/sdc1 /mnt
tar xvfz debian_chroot.tgz /mnt
sudo umount /mnt

```



```
knee@knee-ET1330:~/Downloads$ mount | grep /dev/sdc
/dev/sdc1 on /mnt type ext2 (rw)
knee@knee-ET1330:~/Downloads$ tar xvfz debian_chroot.tgz /mnt
tar: /mnt: Not found in archive
tar: Exiting with failure status due to previous errors
knee@knee-ET1330:~/Downloads$ 



```

---

### Post by papibe on 2012-04-22
To extract a tar on a different location than the actual dir, use the -C option.

This should work:
```
tar xvzf debian_chroot.tgz -C /mnt
```
Tell us how it goes.
Regards.

---

### Post by Kneegrowplease on 2012-04-22
> **papibe said:**
> To extract a tar on a different location than the actual dir, use the -C option.

This should work:
```
tar xvzf debian_chroot.tgz -C /mnt
```
Tell us how it goes.
Regards.


Yay, all it took was a sudo, thank a lot, and thanks to the others!!!

---

### Post by jerome1232 on 2012-04-22
Whoops, a bit hasty in my typing, corrected my original post ;)

---

### Post by Kneegrowplease on 2012-04-22
now how about moving a file???

---

### Post by jerome1232 on 2012-04-22
I'm curious, is there a reason you are not just using nautilus (the default file manager) to do all of this?

---

### Post by Kneegrowplease on 2012-04-24
> **jerome1232 said:**
> I'm curious, is there a reason you are not just using nautilus (the default file manager) to do all of this?


because nautilus is a pain in my ***, if I start it without sudo I don't have permissions on the flash drive, if I start it with sudo, I can't view any of my files (only directories) . (I have to browse to the directory I want to move the file to, then right click and paste something I copied)  reminds me of windows only worse. 



[COLOR="red"]tell me how to make all my files show up when I type sudo nautilus and I WILL use it![/COLOR]

---

### Post by jerome1232 on 2012-04-24
> **Kneegrowplease said:**
> because nautilus is a pain in my ***, if I start it without sudo I don't have permissions on the flash drive, if I start it with sudo, I can't view any of my files (only directories) . (I have to browse to the directory I want to move the file to, then right click and paste something I copied)  reminds me of windows only worse. 



[COLOR="red"]tell me how to make all my files show up when I type sudo nautilus and I WILL use it![/COLOR]

Chown the drive from the command line so your user owns it's file and you won't need sudo nautilus, you can copy the below code verbatim aside from adjusting the part in blue to the real mount point.

```
sudo chown -r $USER:$USER [color=blue]/drives/mount/point[/color]
```


As far as nautilus not seeing your files, that sounds bizarre, I really have no clue as to what may be wrong that that would be happening.

Does starting nautilus like this make a difference? (It's not recommended to use sudo with graphical apps, it can cause permission problems)
```
gksu nautilus
```

---

