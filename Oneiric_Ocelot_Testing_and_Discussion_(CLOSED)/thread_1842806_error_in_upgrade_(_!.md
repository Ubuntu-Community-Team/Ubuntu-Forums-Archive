---
title: "error in upgrade :( !"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Gladiator-prog4me on 2011-09-12
hi , 

when i run update manager , i got this error >> please see the pic in attachment . 

have a nice day

---

### Post by VinDSL on 2011-09-12
I have a *feeling* you won't be the only one...  :(

I've been putting off doing upgrades tonight, because I saw packages on hold.

```

vindsl@Zuul:~$ **[COLOR="Blue"]sudo apt-get update && sudo apt-get upgrade[/COLOR]**
<snip>
Building dependency tree       
Reading state information... Done
**[COLOR="Red"]The following packages have been kept back:[/COLOR]**
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  compiz-plugins-main compiz-plugins-main-default libcompizconfig0
  libdecoration0
The following packages will be upgraded:
  gir1.2-json-1.0 gnome-user-guide libjson-glib-1.0-0 python-compizconfig
**[COLOR="Red"]4 upgraded[/COLOR]**, 0 newly installed, 0 to remove and **[COLOR="Red"]9 not upgraded[/COLOR]**.
Need to get 1,234 kB of archives.
After this operation, 5,800 kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

vindsl@Zuul:~$ **[COLOR="Blue"]sudo aptitude safe-upgrade[/COLOR]**
Resolving dependencies...                
The following packages will be upgraded:
  gnome-user-guide libjson-glib-1.0-0 python-compizconfig 
**[COLOR="Red"]3 packages upgraded[/COLOR]**, 0 newly installed, 0 to remove and **[COLOR="Red"]10 not upgraded[/COLOR]**.
Need to get 1,226 kB of archives. After unpacking 5,796 kB will be used.
Do you want to continue? [Y/n/?] n
Abort.

vindsl@Zuul:~$ 
```
I was going to leave a warning, in the threads, but you beat me to the punch.

Earlier, it was going to remove Unity.  Nasty stuff - partial upgrades!

---

### Post by flipper T on 2011-09-12
dont install partial upgrades.

wait.

---

### Post by cecilpierce on 2011-09-12
Yep, dist-upgrade killed all except for g-classic, took out compiz and put in bzr-compiz which is not working yet  :P
Well I have 2 fall-back OO's  :)

---

### Post by meborc on 2011-09-12
> **flipper T said:**
> dont install partial upgrades.

wait.

+1

You guys always jump the gun. If I have to choose between waiting couple of hours and still having an operable system or doing a partial I always choose the first option.

---

### Post by sgage on 2011-09-12
All the compiz/unity stuff is on the same page now, so you can update. Now there's a bunch of libreoffice stuff being held back, but nothing gets removed...

---

