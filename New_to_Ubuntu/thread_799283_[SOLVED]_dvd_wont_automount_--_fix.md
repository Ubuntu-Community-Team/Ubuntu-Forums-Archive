---
title: "[SOLVED] dvd wont automount -- fix?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Bodsda on 2008-05-18
Hi guys, im having a problem, like the title says my dvd drive does not automount. and if i mount it manually it doesnt work in cedega. my gutsy install worked like a charm but im having quite a few probs with hardy.im running hardy amd 64. This is the error when i try and click on my dvd drive from 'Places'

Cannot mount volume.

Invalid mount option when attempting to mount the volume 'INSTALL'.

========
And this is the error from cedega

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


output of sudo fdisk -l -- [http://paste.ubuntu.com/13215/]("http://paste.ubuntu.com/13215/")
contents of /etc/fstab  -- [http://pastebin.com/f34698933]("http://pastebin.com/f34698933")

Thanks in advanced

---

### Post by spiderbatdad on 2008-05-18
Bodsda, thinking look in dmesg. cdrom0 may actually be cdrom1...as an example I found in tis post:[http://backports.ubuntuforums.com/showthread.php?t=731223](http://backports.ubuntuforums.com/showthread.php?t=731223) Remove the offending line from fstab

---

### Post by Bodsda on 2008-05-18
fixed by removing the automount line in /etc/fstab 

sounds a bit stupid removing the line that automounts things but oh well

thanks spiderbatdad

---

