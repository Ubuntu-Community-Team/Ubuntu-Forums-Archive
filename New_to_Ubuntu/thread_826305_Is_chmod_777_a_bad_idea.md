---
title: "Is chmod 777 a bad idea?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by brallan on 2008-06-11
I had 3 internal drives on a windows machine, the windows disk and 2 ntfs disks with data. I decided to switch to Ubuntu. I backed up my internal ntfs drives, wiped my windows partition, installed ubuntu in the first drive, formatted to ext3 and added two lines to my fstab:

```
/dev/sdb1 /media/Archives ext3 defaults 0 0
/dev/sdc1 /media/Personal ext3 defaults 0 0 
```

after a rather frustrating period of root owning the drives and failing to change things using gksu nautilus, i chmodded it all to 777 recursively, for example using

```
 sudo chmod 777 -R /media/Archives 
```

after which it all worked like a charm.

but then I read.......

> Never, ever, ever use 777. Just don't. It's wrong, dangerous, and a source of trouble. If you ever think you need to use 777 (or 666) for anything, stop a second and backup, as you likely made a mistake elsewhere.

am I going to have problems with this?

---

### Post by Sef on 2008-06-11
> am I going to have problems with this?

Not necessarily.  cmmod 777 is useful, if you know what you are doing, but you can mess up your system with it too.  In your case, since things are working, I would not worry.

---

### Post by gr4nf on 2008-06-11
Try just using the "sudo" prefix on whatever you need to do. i.e.:
```

sudo mke2fs -j /dev/sda

```
dont do that, by the way.

---

### Post by Darkade on 2008-06-11
As sef said you shouldn't have any problem. chmod 777 is a bad idea when you use it in system files say /usr or /bin or /boot
but since those are user files there shouldn't be any problem. However you might first to run
```
sudo chown -r youruser /media/whatever
```
and then do
```
chmod -r 774 /media/whatever
```
so that you are the owner of those files and only your user can modify them

BTW gr4nf why to post something you don't want them to run?

---

### Post by Joeb454 on 2008-06-11
> **gr4nf said:**
> Try just using the "sudo" prefix on whatever you need to do. i.e.:
```

malicious command :(

```
dont do that, by the way.

If you don't want them to run it, why post it??

If you want to give an example of the use of "sudo" then use ```
apt-get install xchat
``` Say how this gives an error (maybe post it) and then show that ```
sudo apt-get install xchat
``` Does in fact work.

---

### Post by miss.magenta on 2008-06-11
The better solution would be to edit your fstab entry to be more like (this is my fstab, obviously your mountpoints will be different):

```
/dev/sdb1	/media/sdb1	ext3	rw,user,exec		0	0
/dev/sdb2	/media/sdb2	ext3	rw,user,exec		0	0
/dev/sdc1	/media/sdc1	ext3	rw,user,exec		0	0
/dev/sdc2	/media/sdc2	ext3	rw,user,exec		0	0

```

...do so and you should not have to worry about chowning and chmoding anything.

---

### Post by brallan on 2008-06-14
Wow, thanks so much for all your help people. I found out that its better to use /mnt/ rather than /media/ as a mount point, otherwise there is an icon on my desktop & in the disk mounter applet to the drive.

---

