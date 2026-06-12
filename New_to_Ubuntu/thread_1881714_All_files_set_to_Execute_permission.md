---
title: "All files set to Execute permission"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by greendragons on 2011-11-16
Hiii,
I have a ntfs partition whose entry i have added in fstabs so tht it can be mounted automatically...
the problem is that it's all files are set to execute permission automatically.... i don't know whether it is because of mask i set in fstabs or some other reason....

fstab entry for that partition
```

UUID="BE5A8D685A8D1E71" /media/CRUTIAL_CLUTCHES           ntfs defaults,nls=utf8,umask=033,uid=1000,windows_names  0    0


```
How to remove execute permission from those files.. and also whenever i create new file it is also set to execute permission automatically.....

Thnx!!

---

### Post by SheaMan on 2011-11-16
Hi! :D
I have a ntfs partition whose entry I have added in fstabs so that it can be mounted automatically. The problem is that it's 'all files' are set to execute permission  automatically. I don't know whether it is because of the mask I set in  fstabs or some other reason..... :confused:

fstab entry for that partition
 	Code:
 	UUID="BE5A8D685A8D1E71" /media/CRUTIAL_CLUTCHES           ntfs defaults,nls=utf8,umask=033,uid=1000,windows_names  0    0 
How to: remove execute permission from these files. :confused: and also  whenever I create a new file


[quote=you]
 it is also set to execute permission  automatically.....
[/quote]

Thnx!!

[quote=me]
wtf does that mean?
[/quote]

---

### Post by greendragons on 2011-11-16
> **SheaMan said:**
> Hi! :D
I have a ntfs partition whose entry I have added in fstabs so that it can be mounted automatically. The problem is that it's 'all files' are set to execute permission  automatically. I don't know whether it is because of the mask I set in  fstabs or some other reason..... :confused:

fstab entry for that partition
     Code:
     UUID="BE5A8D685A8D1E71" /media/CRUTIAL_CLUTCHES           ntfs defaults,nls=utf8,umask=033,uid=1000,windows_names  0    0 
How to: remove execute permission from these files. :confused: and also  whenever I create a new file




Thnx!!

It means whenever i create any file it is automatically set to executable....

---

### Post by SheaMan on 2011-11-16
:-k thaaasa.. file permission value thing right? Like 777 attributes? :popcorn: idk ;)

:uuhm: Why wouldnt a file be set to executable by default? :confused:

---

### Post by greendragons on 2011-11-16
> **SheaMan said:**
> :-k thaaasa.. file permission value thing right? Like 777 attributes? :popcorn: idk ;)

:uuhm: Why wouldnt a file be set to executable by default? :confused:
It's probably the mask problem....

---

