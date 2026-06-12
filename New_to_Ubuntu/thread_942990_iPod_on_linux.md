---
title: "iPod on linux"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-10-09
I have been using linux for a while. I just got an iPod and I heard linux supported it. Well the problem is that I get Amarok configured to the iPod but it says that its lockfile or something like that. Is there anything I can do to get it to work?

---

### Post by SunnyRabbiera on 2008-10-09
Newer ipods are more tricky then older ones I will warn you, I think most newer ipods need to be jailbreaked before you could use them.

---

### Post by SuperSonic4 on 2008-10-09
SunnyRabbiera is right, you need to see which model you have. My method below works on my 5th/6th generation classic

delete: /media/iPod/iPod_Control/iTunes/iTunesLock (or something similar)

```
rm -vi /media/iPod/iPod_Control/iTunes/iTunesLock
```

where iPod is the name of your iPod (mine is *Sonic's iPod* xD)

the v means to tell you what you're doing and i means prompt for confirmation

If you need to be root:

```
sudo rm -vi /media/iPod/iPod_Control/iTunes/iTunesLock
```

---

### Post by deadlySniper on 2008-10-09
There is no iTunes Lock. There is iTunesControll but I cant delete it since its a read only. Also I tried gtkpod and it has the same problem

---

### Post by deadlySniper on 2008-10-09
I tried the code and it doesnt work

---

