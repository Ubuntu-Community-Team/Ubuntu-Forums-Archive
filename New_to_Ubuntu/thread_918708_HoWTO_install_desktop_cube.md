---
title: "HoWTO install desktop cube"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-09-13
Hellow

I tried to install compiz on my ubuntu
but if i try to open the file i downloaded (compiz-0.6.2-2.i486.rpm) it says he cant find the opening file

what should i do now?

mvg,
Dadsgé

---

### Post by SuperSonic4 on 2008-09-13
Isn't compiz installed by default?

Try pressing alt+f2 and typing ccsm into the box, if it loads it will be installed. In GNOME I think it's in System -> Appearance -> Desktop Effects

---

### Post by emshains on 2008-09-13
Try ```
sudo apt-get install cssm compiz
```

That should do it. Also you can right click the desktop,then  choose "Change background" and then you should pick "Visual Effects". Don't know if the labels are correct, cause I did a rough translation from my language.

---

### Post by Dadsgé on 2008-09-13
if i try the Alt+F2 and typing ccsm, then hit 'RUN'
it says: 'Could not open location 'file:///home/hannes/ccsm'

and under system->appearance i dont find any desktop effects...

---

### Post by Dadsgé on 2008-09-13
in the terminal it gives
> reading packet list... done
reading state information...done
E: couldn't find packet ccsm

---

### Post by Nepherte on 2008-09-13
It's
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by ooobuntooo on 2008-09-13
Look for "Advanced Desktop Effects Settings" in the repos!

---

### Post by Rhubarb on 2008-09-13
The cssm package does not actually exist.  Hence the errors you get.

The correct package is:
```
sudo aptitude install compizconfig-settings-manager
```
If compiz is not enabled, do so:
System --> Preferences --> Appearance --> Turn on Visual Effects.

Then if you want a cube, you can configure it here:
System --> Preferences --> CompizConfig Settings Manager

---

### Post by Drakkor on 2008-09-13
Or,if you want the newest one with cylinder or sphere,instead of just cube
you can find it here:
[http://64.233.169.104/search?q=cache:http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/&hl=en&lr=&c2coff=1&sa=G&strip=1](http://64.233.169.104/search?q=cache:http://tombuntu.com/index.php/2008/07/25/upgrade-to-the-latest-compiz-fusion-release/&hl=en&lr=&c2coff=1&sa=G&strip=1)  :)

---

### Post by Dadsgé on 2008-09-13
thanx, its working ^^

---

