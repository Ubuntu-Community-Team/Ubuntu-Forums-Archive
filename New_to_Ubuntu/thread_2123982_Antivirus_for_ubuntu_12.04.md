---
title: "Antivirus for ubuntu 12.04"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by user_linux on 2013-03-09
Hi,
What happended to Klam AV antivirus? I don't see that in software centre. Where can I intsall that?
thx!

---

### Post by The Spectre on 2013-03-09
It is spelled Clam.

---

### Post by Mr. Shannon on 2013-03-09
I think you mean Clam AV.
```
sudo apt-get install clamav
```
if you want a GUI then
```
sudo apt-get install clamtk
```

---

### Post by user_linux on 2013-03-09
> **Mr. Shannon said:**
> I think you mean Clam AV.
```
sudo apt-get install clamav
```
if you want a GUI then
```
sudo apt-get install clamtk
```

I got this output:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But when I typed clamav i don't see in my system?

---

### Post by cheatos on 2013-03-09
its because it is a commad line tool.
You may want to install the frontend for clamav (dont know the exact name, do a quick google for clamav, or look it up in the ubuntu wiki its there as well)

ok, the name of the frontend is clamtk. you can install it with
```
sudo apt-get install clamtk
```

---

### Post by user_linux on 2013-03-09
ok, i did, but i can't find the old layout like scheduled scan facilties and more update options, where is everything? This ubuntu is so different from previous versions.

> **cheatos said:**
> its because it is a commad line tool.
You may want to install the frontend for clamav (dont know the exact name, do a quick google for clamav, or look it up in the ubuntu wiki its there as well)

ok, the name of the frontend is clamtk. you can install it with
```
sudo apt-get install clamtk
```

---

### Post by oldos2er on 2013-03-09
Klamav hasn't been in the repositories for a long time, I'm assuming it's no longer being developed or supported. For those wondering, klamav was a KDE frontend for ClamAV.

---

### Post by Larkspur on 2013-03-09
> **user_linux said:**
> ok, i did, but i can't find the old layout like scheduled scan facilties and more update options, where is everything? This ubuntu is so different from previous versions.

Either:

1. Move your mouse to the top of the screen and select "Advanced", or;
2. Press the Alt key once and begin typing "Preferences" or "Scheduler".

---

### Post by deadflowr on 2013-03-09
```
man clamtk
```

```
man clamscan
```

---

### Post by user_linux on 2013-03-09
> **Larkspur said:**
> Either:

1. Move your mouse to the top of the screen and select "Advanced", or;
2. Press the Alt key once and begin typing "Preferences" or "Scheduler".

Great, thanks! I didn't realize the new ubuntu has everything at top.

---

