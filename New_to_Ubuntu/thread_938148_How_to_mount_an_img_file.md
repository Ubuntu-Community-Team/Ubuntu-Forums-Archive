---
title: "How to mount an img file?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by EddieBarzoon on 2008-10-04
I want to download the drivers for a IBM ServRaid 4 device in order to inject them in to a LinuxPE disk so I can recognize the hard disk for imaging.

I have found the driver at - [https://www-304.ibm.com/systems/support/supportsite.wss/docdisplay?lndocid=MIGR-5072186&brandind=5000019](https://www-304.ibm.com/systems/support/supportsite.wss/docdisplay?lndocid=MIGR-5072186&brandind=5000019)

I have downloaded the IMG file but I am unable to mount this to get at the actual files.

I have used the command:
sudo mkdir /mnt/test
sudo mount -t iso9660 -o loop /home/eddie/Desktop/39y4880.img /mnt/test

this fails with:
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


How can I mount this img file?

Thanks in advance for any responses.

---

### Post by NESFreak on 2008-10-04
though i have no experience with this piece of software myself, you should just be able to mount it after installing fuseiso. It's in the repositories. > FUSE module to mount ISO filesystem images
This package provides a module to mount ISO filesystem images
using FUSE.
With FUSE it is possible to implement a fully functional
filesystem in a userspace program.

It can also mount single-tracks .BIN, .MDF, .IMG and .NRG.

 Homepage: [http://fuse.sourceforge.net/wiki/index.php/FuseIso](http://fuse.sourceforge.net/wiki/index.php/FuseIso)

---

### Post by eldragon on 2008-10-04
i think the command is
```

$ sudo mount -o loop image.img /mnt/mount_point

```

---

### Post by niteshifter on 2008-10-04
Hi,

Those appear to be floppy disk images. Try this:

```
sudo mount -o loop /home/eddie/Desktop/39y4880.img /mnt/test
```

---

### Post by EddieBarzoon on 2008-10-05
Thanks niteshifter - that worked!

So the incorrect part of the command was the "-t iso9660" which refers to a CD file system.

---

