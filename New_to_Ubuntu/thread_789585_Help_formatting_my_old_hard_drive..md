---
title: "Help formatting my old hard drive."
date: 2008-05-10
forum: New to Ubuntu
---

### Post by aknisely on 2008-05-10
I just installed my new hard drive and installed 8.04. I have my old drive set as a slave but it still has all of the old system files on it. Is there a way I can erase that all without having to go through all the trouble of reformatting and mounting?

I tried the formatting and mounting before I installed 8.04 but I couldn't get it to work out. Thanks!

---

### Post by Journeyman on 2008-05-10
Use gparted to create a parition and format

```
 apt-get install gparted 
```

---

### Post by aknisely on 2008-05-10
This wont cause any mounting problems will it? I reformatted the new one when I was using the old drive as the master and couldn't get it to mount. I reformat it as ext3 right?

---

### Post by thisiam on 2008-05-10
check out [DBAN]("http://http://dban.sourceforge.net/") and burn the ISO and go from there. no formatting needed, well dban will do it for you but all you have to do is press enter to nuke. 

WARNING: make sure you only delete the slave drive and not your linux drive.

---

### Post by aknisely on 2008-05-10
I keep getting an error in Geparted so I cant reformat it to ext3.:confused:

---

### Post by Journeyman on 2008-05-13
what error are you getting?

---

