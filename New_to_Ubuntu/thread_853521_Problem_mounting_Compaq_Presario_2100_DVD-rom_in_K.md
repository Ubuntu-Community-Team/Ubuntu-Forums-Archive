---
title: "Problem mounting Compaq Presario 2100 DVD-rom in Kubuntu"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by xJippu on 2008-07-08
Hey!

I'm new to linux, I've been running Kubuntu in my old laptop (Compaq Presario 2100) for about two weeks now. The system just doesn't seem to recognise the DVD-rom of the laptop.

Symptoms & facts:

When inserting an audio-cd and looking it up in Dolphin &#8594; Storage media, the ”Audio-cd” symbol appears, but when you klick it, there's only an error saying ```
Could not start process Unable to create io-slave: klauncher said: Unknown protocol 'audiocd'
```

So I checked the /etc/fstab with Kate. The contents:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=260df777-8777-4c9c-b7a6-094c9326f422 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=05ed63c8-3e2d-4f17-a75b-104c91032bad none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,auto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Okay, the cdrom seems to be there, at /dev/hdc/media/cdrom0. Tried to mount it, got following:

```
username@computername:~$ mount /dev/hdc/media/cdrom0
mount: /dev/hdc/media/cdrom0 ei löydy tiedostosta /etc/fstab, eikä /etc/mtab
username@computername:~$ mount /dev/cdrom0
mount: /dev/cdrom0 ei löydy tiedostosta /etc/fstab, eikä /etc/mtab
username@computername:~$ mount /media/cdrom0
mount: lohkolaite /dev/hdc on kirjoitussuojattu, liitetään vain luku -tilassa
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or helper program, or other error
       Joissakin tapauksissa järjestelmälokista löytyy hyödyllistä
       tietoa - kokeile esim. komentoa ”dmesg | tail”.
```

username@computername:~$

any ideas what to try next? Sorry for the long post, tried to give as much valid information as possible.

P.S. Sorry, I noticed that some of the codes are in finnish since my kubuntu is a finnish trnslation, ask if theres any translation misunderstanding.

---

### Post by ChameleonDave on 2008-07-08
> **xJippu said:**
> 
```
mount /dev/hdc/media/cdrom0
```
That command is wrong.

You mount something somewhere, with a space in between.  However, if the entry is in fstab, you only need to specify one part of that: "mount /dev/hdc" or "mount /media/cdrom0", as you did afterwards.

---

### Post by ChameleonDave on 2008-07-08
Looking at it again, I can see that "/dev/hdc" is highly unlikely to be the correct identifier for your optical drive.

Please paste the output of the following commands:

```

sudo blkid
sudo lshw -sanitize

```

---

