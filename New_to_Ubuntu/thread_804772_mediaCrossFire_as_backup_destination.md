---
title: "/media/CrossFire as backup destination"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by grikdog on 2008-05-23
I have a CrossFire external hd which appears and mounts correctly (apparently) on my desktop.  However, when I point System -> Administration -> Simple Backup Config to the CrossFire drive, something confusing happens.  It seems that my backups have been written to a directory called /media/CrossFire and NOT to an external hard drive whose mount point is /media/CrossFire.  To illustrate, at this moment, the CrossFire drive is unmounted (and turned off), but ALL MY BACKUP FILES ARE PRESENT in the /media/CrossFire directory -- i.e., they appear in the regular file system.  Does anyone know what is going on, and how to fix the error?  It makes absolutely no sense to backup onto the same medium as the original files!

---

### Post by quelx on 2008-05-23
try this

With the drive unplugged and from the terminal

```
sudo mv /media/CrossFire /media/temp
```

Plug the CrossFire in and make sure it gets mounted at /media/Crossfire

```
mount
```

should see some line /dev/sdc1 /media/CrossFire or something of that sort

Now move everything back to the external drive

```
sudo mv /media/temp/* /media/CrossFire/
```

Set up your backup again and see what happens, it looks like the backup ran without the drive attached (maybe that's obvious)

---

### Post by grikdog on 2008-05-23
Not so obvious, maybe.  I'm used to Windows Vista (SP1) and Mac OS X 10.4 where the *systems* look before they leap ;-)

Anyway, thanks for the clarity!  Maybe I should write my own script to check for [ -x /media/CrossFire ] first?  Is there a better way than Simple Backup Config?  Does Ubuntu have Anacron?  This laptop (Dell Inspiron 1525) does not run 24/7, and the CrossFire is not usually attached.

---

### Post by quelx on 2008-05-23
Maybe manual backups are more suited to your situation since the drive isn't always there (and sbackup can't make that determination)  I noticed simplebackup does support that function.

---

