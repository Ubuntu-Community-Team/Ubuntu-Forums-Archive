---
title: "linux nero warning message"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by k66473 on 2008-05-06
Hi, when I start nero linux, I get following warning
[I]```
One of your devices is not accessible.
Please check that you have correct permissions on the corresponding device file. Nero Linux can not get access to the following devices:
/dev/sg0 (SCSI generic device)

```[/I]
This is my fstab info
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=44ca24ba-7445-4ee9-abb4-c4f8f43bef88 / ext3 relatime,errors=remount-ro 0 1
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
#
#added by minhtdvn for auto mount NTFS
#
/dev/sda2 /media/D ntfs-3g defaults 0 0
/dev/sda3 /media/E ntfs-3g defaults 0 0
#
#added by minhtdvn for swap purpose
#
/swap.img none swap sw 0 0
```

If I start nero linux by command "sudo nero" then no warning appears
I tried to change permission of file /dev/sg0 to 666 then problem gone away. But when the system restarts, everything I changed was turned back (permission turned back to 660). This issue just happen to me.
Please give me some hints

---

### Post by Xiong Chiamiov on 2008-05-06
What if you change
```

/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```
to
```

/dev/hda /media/cdrom0 udf,iso9660 defaults 0 0

```

Aside from that, why are you using Nero?  Kubuntu I know comes with an excellent burning tool (K3B), and I assume Ubuntu does as well.

---

### Post by ichbinesderelch on 2008-05-06
in what groups is your user in? maybe output of "gropus username" would help
otherwise try using k3b for example for burning cds

---

### Post by k66473 on 2008-05-06
> minhtdvn@aspire:~$ groups minhtdvn
minhtdvn adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
minhtdvn@aspire:~$ 
I am updating my answer

---

### Post by ichbinesderelch on 2008-05-06
try adding your user to optical grp by gpasswd -a minhtdvn optical, maybe this will do the trick

---

### Post by k66473 on 2008-05-06
I am sure but this trouble appear after I install total commander (ghisler.com) via wine. At that time, my system does not recognize the DVD writer.

When I remove total commander and clean up my harddisk (at that time, my harddisk is full), DVD writer come back and I am not sure which action does the trick.

---

### Post by k66473 on 2008-05-06
I am sure but this trouble appear after I install total commander (ghisler.com) via wine. At that time, my system does not recognize the DVD writer.

When I remove total commander and clean up my harddisk (at that time, my harddisk is full), DVD writer come back and I am not sure which action does the trick.

---

### Post by brewstah on 2008-05-07
I got an error message like that when I first tried Nero Linux 2.  But I just ignored it and burned some discs anyway.  According to Ahead, NL2 had some bugs in how it interacted with the IDE drivers...something like that.  The problem was fixed with version 3.x.

---

