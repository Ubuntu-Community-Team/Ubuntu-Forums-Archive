---
title: "Cannot Mount UDF?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by 4n4lys1s on 2008-06-09
What does can not mount to volume UDF mean? Whenever I put in a DVD-R, It gives me that message! Heeeeelp!

---

### Post by Baelus on 2008-06-09
All I can offer is a way to mount from the command line.

```
sudo mount -t udf -o loop /dev/[DVD Drive] /media/[Mount Folder]
```

I think that's right.

The [DVD Drive] will probably be something like /dev/cdrom or /dev/cdrom0 or /dev/scd0 or something like that. Have a look in /etc/fstab and it should have been put there automatically.

And [Mount Folder] will be a folder in /media/ that you created.

Hope it works out.

- B

PS If the disc was burned in Vista then others are also having problems mounting the UDF filesystem on DVDs.

[http://ohioloco.ubuntuforums.org/showthread.php?t=650697]("http://ohioloco.ubuntuforums.org/showthread.php?t=650697")

---

