---
title: "[SOLVED] need to uninstall MSFONTS completely"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by macvr on 2008-08-16
hi, i installed msttcore fonts and clear type vista fonts in my system but it didnt turn out well , they are not rendered properly, so i decided to uninstall them completely 

but i'm not able to ... i'v done 

```
sudo apt-get purge msttcorefonts

sudo apt-get --purge remove msttcorefonts

```
i have also removed cabextract which i had added with vista clear fonts

but  still the fonts persist... how do i completely remove these fonts?

---

### Post by LowSky on 2008-08-16
try sudo apt-get remove msttcorefonts*

---

### Post by JillSwift on 2008-08-16
Rebuild your font cache:
```
fc-cache --force
```

---

### Post by macvr on 2008-08-16
> **LowSky said:**
> try sudo apt-get remove msttcorefonts*


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting msttcorefonts for regex 'msttcorefonts*'
E: Couldn't find package msttcorefonts*

```

this is what i got but still i see the fonts

---

### Post by macvr on 2008-08-16
> **JillSwift said:**
> Rebuild your font cache:
```
fc-cache --force
```

did this but still they are there...!!!:confused:

and i also did the re-log in everytime:(

---

### Post by JillSwift on 2008-08-16
> **macvr said:**
> did this but still they are there...!!!:confused:

and i also did the re-log in everytime:(I'd guess this means the fonts are still installed. Have a look in ~/.fonts for them, and in /usr/share/fonts/ (This is where they will *likely* be, in the directory /usr/share/fonts/truetype/msttcorefonts/)

(You'll need to use "gksu nautilus" from a command line to be able delete anything in /usr/share/fonts - **[COLOR=Red]be cautious[/COLOR]**.)

Once you have them removed, rebuild the font cache again.

---

### Post by macvr on 2008-08-16
> **JillSwift said:**
> I'd guess this means the fonts are still installed. Have a look in ~/.fonts for them, and in /usr/share/fonts/ (This is where they will *likely* be, in the directory /usr/share/fonts/truetype/msttcorefonts/)

(You'll need to use "gksu nautilus" from a command line to be able delete anything in /usr/share/fonts - **[COLOR=Red]be cautious[/COLOR]**.)

Once you have them removed, rebuild the font cache again.

ya was doing _gksudo nautilus_ just this while u posted , both are the same right?

the damn fonts where in the  /usr/share/fonts/ folder itself!!! 

and to rebuild i did this

```
sudo fc-cache -f -v
```

is it all correct ?
fonts are gone though, its just that i'm a noob n did a mix of a few things i found here and there!!!

---

