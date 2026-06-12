---
title: "permanently mounting drives"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-27
I wanna mount a drive, and i was looking at fstab to try to work off of that. and:
```

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

i understand what the 'media/floppy0 auto' is, but whats that other stuff?
if my the drive i want to have permanently mounted is at /media/presario, would the code just be

```
/dev/fd0        /media/presario  auto    rw,user,auto,exec,utf8 0       0
```

also, i put firestarter to my app startup list, but it asks for my password when ubuntu is booting up, is there a way around this, because my dad sometimes gets on here and he won't be able to get on.

---

### Post by Het Irv on 2008-05-27
No, that line wouldn't work

The first section is the mount point, for a drive that would be something like "/dev/hd1" or something like that.  

The second section is where you are mounting to, that part should work as long as the folder exsists when you try to mount. 
The rest should work, thats permissions stuff like that.

```
sudo fdisk -l
```
Post the output of this command and I should be able to help a little more.

---

### Post by Duck2006 on 2008-05-27
Some reading on mounting drives.
For windoze

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

for linux

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by tuga on 2008-05-30
Thank you Duck2006. The link to linux worked fine.

---

