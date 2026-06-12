---
title: "backing up important data"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by techno-mole on 2008-09-04
hello.
im looking into automatically backing up some files in my home directory, there are some options open to me, but from what ive read using dar seems to be the best, or at least a safe way to do it.

so does anyone know of a simple how to that shows you how to use it, ive looked on the dar website and to be honest i got a little confused, what i want to try and do is either back up the files onto the file serve i built, or back the files up to an external hard drive.

i couldnt seem to find anything relating to what i want to do, and it also seems that some of these tools dont support backing up to external devices and such like, which is a little odd.

any help will be appreciated.

---

### Post by frank002 on 2008-09-04
I just back up my Home directory and other important stuff on my 2nd hard drive. I tried Simple Backup once but did not care for it.  Some people advocate having a separate Home partition. That way, if you reinstall, you format the other partitions but keep that Home partiton and your data.

---

### Post by quibbler on 2008-09-04
> **techno-mole said:**
> hello.
im looking into automatically backing up some files in my home directory, there are some options open to me, but from what ive read using dar seems to be the best, or at least a safe way to do it.

so does anyone know of a simple how to that shows you how to use it, ive looked on the dar website and to be honest i got a little confused, what i want to try and do is either back up the files onto the file serve i built, or back the files up to an external hard drive.

i couldnt seem to find anything relating to what i want to do, and it also seems that some of these tools dont support backing up to external devices and such like, which is a little odd.

any help will be appreciated.
Try Quickstart, I think that will do what you want.

[http://quickstart.phpbb.net/index.php?sid=d1f9bea05efa1b8e63a2bb7dec65f694](http://quickstart.phpbb.net/index.php?sid=d1f9bea05efa1b8e63a2bb7dec65f694)

Regards quibbler

---

### Post by ghostdog74 on 2008-09-04
common method
```

tar cf home.tar /home
gzip home.tar
mv home.tar.gz /media/usb
rm home.tar 

```

---

### Post by kpkeerthi on 2008-09-04
I don't prefer to use tar for backing up my home for the simple reason that I have loads of MP3s, Pictures, large ISOs, etc. Having tar/bzip compress files of these sort is pointless as these files are already in compressed format and will simply eat time and CPU. I just use [rsync]("https://help.ubuntu.com/community/rsync") for this purpose.

```

rsync -a /home/<user> /media/disk/backups

```

* /media/disk is where my backup disk is mounted.

Simply add the command to your [crontab]("https://help.ubuntu.com/community/CronHowto") and you are done

---

