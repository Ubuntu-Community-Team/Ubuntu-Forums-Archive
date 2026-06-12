---
title: "I cant mount an external hard drive as read only, it has windows 8"
date: 2014-08-15
forum: New to Ubuntu
---

### Post by bug3 on 2014-08-15
i know this problems solves by restarting with windows 8 in  an normal mode, but i dont have anymore any windows 8, im trying to  rescue the files that i had in a laptop that it motherboard burned out,  and i cant install windows 8 in this one, i only have ubuntu on this  machine.

  the message i get when i try to open this external hard drive is:

  Error mounting /dev/sdb4 at /media/bug/52B0E048B0E0345F: Command-line  `mount -t "ntfs" -o  "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177"  "/dev/sdb4" "/media/bug/52B0E048B0E0345F"' exited with non-zero exit  status 14: The disk contains an unclean file system (0, 0). Metadata kept in Windows cache, refused to mount. Failed to mount '/dev/sdb4': Operation not permitted The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option.
  ¿how can i recover my files from ubuntu? it says that i can mount  the volume as ro but i dont know how to do that, and i dont know it that  would allow me to copy my files

  

  im tryin to mount it from terminal as:sudo mount -o ro /dev/sdc4 at /media/bug/

  but i only get information about mount command, what am i doing wrong?

thanks for your time

---

### Post by Sanctimonious_Ape on 2014-08-15
[FONT=Fixedsys]If you're actually typing that "at" word before the mount point, that might be the cause.  Try:
```

sudo mount -t ntfs-3g -o ro,noatime,nls=utf8,umask=0222 /dev/sdc4 /media/bug

```
[/FONT]

---

### Post by bug3 on 2014-08-15
thaks sanctimonious! that solved it, i thought i had to write it that way because with out it it said that the directory didnt existe, but i copied what you wrote and it worked, sorry for my english still learning

---

### Post by Sanctimonious_Ape on 2014-08-15
Your English was fine (I know plenty of "native-speakers" who unfortunately can't speak that well, either :rolleyes:).  Glad it worked for you and good luck with your file recovery.

---

