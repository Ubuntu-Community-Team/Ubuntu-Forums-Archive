---
title: "cannot mount volume?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by missionventure on 2008-10-01
I just installed ubuntu 8.04.1, and when I go to my External HD I get this  
[IMG]http://img505.imageshack.us/img505/5299/27798833gx1.jpg[/IMG]
so I tried doing what it said in the terminal? 

mount -t ntfs-3g /dev/sdc1 /media/OneTouch 4 -o force

and got:

mount: only root can do that

No idea what to do..Earlier today, before I installed 8.04, I was using 6.06, and I could open the drive, view files, listen to music..but I couldn't remove/add files from the drive =/  now I simply cant do anything..any ideas?

---

### Post by Elfy on 2008-10-01
> mount: only root can do thatuse sudo

```
sudo mount -t ntfs-3g /dev/sdc1 /media/OneTouch 4 -o force
```

You might be better of if you are dual booting to do Choice 1

---

### Post by vanadium on 2008-10-01
Use choice 1: repair the disk using Windows. -o force mounting is only useful for emergency. Linux does not mount an "unclean" disk because mounting and writing to it involves a risk for further damage.

---

### Post by missionventure on 2008-10-01
I deleted windows completely. 

I put sudo in, and now ive got this huge list of things..no idea what to do, Sorry, I am a complete beginner...gotta learn sometime though

---

### Post by nothingspecial on 2008-10-01
Install this
```
sudo apt-get install ntfsprogs
```

Then fix your drive like so

```
sudo ntfsfix /dev/sdc1
```

---

### Post by missionventure on 2008-10-01
ah, that worked..thank you soooo much :)

---

### Post by nothingspecial on 2008-10-01
cool

:guitar:

---

