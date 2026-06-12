---
title: "Disk space concerning Wine"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Nevyn on 2008-07-14
I've tried searching for this problem (including the Wine-docs, but maybe I too impatient) but struck zero (although finding the inconclusive [http://ubuntuforums.org/showthread.php?t=179565](http://ubuntuforums.org/showthread.php?t=179565)). 
It's probably one of those problems that's so easy that one misses it's obviousness.

Problem:
Never tried Wine before, have it installed and updated...but when I tried installing the bought games Oblivion and Half-Life 2, it says I don't have enough disk space. How do I change the disk space Wine is allowed to use? I failed at finding an option to change this in "Configure Wine".

Thanks!

---

### Post by tramir on 2008-07-14
As far as I know, Wine uses the available space on your hd, there's no "limit" imposed to it. Can you copy/paste the output of the following command in a terminal window:

```
df
```

---

### Post by weirdfox on 2008-07-14
Usualy wine will take the space from your home folder and will install it's stuff in the folder ~/.wine/drive_c.

If you don't have enough disk space on that partition, you can change your wine drive to another disk and replace the ".wine/drive_c" folder with a symbolic link to the new location.

If you need to find out which drive have enough space left, you can always use (in a terminal) "df -h".

I hope this helps !

---

### Post by ChameleonDave on 2008-07-14
A cool way of seeing how much space you have and what is occupying it is to install "filelight" and use it to view things graphically.

---

### Post by Nevyn on 2008-07-14
Thanks Weirdfox! Didn't realize Wine took space from my /home-folder (it's on a separate partition from my main filesystem). It worked perfectly!

---

