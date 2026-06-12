---
title: "Botched KDE Installation"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-06
Hi folks, 

So I used the command 

```
sudo aptitude install kubuntu-desktop
```

to try to install KDE so as to have both GNOME and KDE. The install hung at a point... was downloading some file and it froze at some percentage and didn't budge... so I closed the terminal window.... Bad. 
So I'm assuming that now there's a bunch of uninstalled crap/other files on my system which I want to get rid of. What to look for/how to do?

I did run


```
sudo aptitude uninstall kubuntu-desktop
```

And that took out like... one file but I'm still assuming there's a lot there. 

OR, if I re run the sudo aptitude install command will that fix everything??

(It seems that I've been having the worst luck with linux lately)... 

Thanks, 

-'Mage

---

### Post by spiderbatdad on 2008-05-06
maybe ```
sudo apt-get autoremove
```

---

### Post by cwgatling on 2008-05-06
And maybe a ```
sudo apt-get autoclean
``` ?

---

### Post by UnWarierMage224 on 2008-05-06
I just tried that... It tells me that kubuntu-desktop is not installed, so it didn't remove anything. 

```
 sudo apt-get autoremove kubuntu-desktop
```

-'Mage

---

### Post by spiderbatdad on 2008-05-06
dont add any extra commands:
```
sudo apt-get autoremove
sudo apt-get autoclean
```

---

### Post by UnWarierMage224 on 2008-05-06
Ran both those commands... they executed OK. 

Did a search for KDE, Kubuntu, Kaffeine - a few program names I remember popping up during install... there's still some stuff left in the usr/share directory... I'm assuming that that's OK to leave hanging around?

Can I try reinstalling KDE using the first command (aptitude install kubuntu-desktop)? 

Thanks, 

-'Mage

---

### Post by tubezninja on 2008-05-06
You could also try

```
sudo apt-get purge kubuntu-desktop
```


The repositories are quite slow today.  Are this still the result of people install/upgrading to Hardy?

---

### Post by cwgatling on 2008-05-06
Good point. There are a lot of post about it here today. It might be worth waiting for a bit before trying to DL kubuntu again. Or try using the torrent [HTML]http://torrent.ubuntu.com/kubuntu/releases/hardy/release/dvd/[/HTML]?

---

### Post by kansasnoob on 2008-05-06
Have you tried just opening Synaptic, clicking Reload, and seeing if there are any "broken" packages?

If not (I'm assuming you're using Hardy), you could then click on "search" and type in: ubuntu-desktop ............ then choose to reinstall. It may "pull in" some missing packages.

If not you may be able to run "recovery mode" from GRUB.

---

### Post by UnWarierMage224 on 2008-05-06
@ kansas: I am still able to use GNOME as I never uninstalled Gnome in the first place.... I just checked synaptic and it says that KDE is not installed even though there's still a bunch of crap in my usr/share folder from the botched KDE install (icons and the like)

@ everyone else: Thanks to all for the advice. I will most likely try to redownload KDE on another day. 

-'Mage

---

### Post by kansasnoob on 2008-05-06
Oops more replies while I was typing and tending to other fires.

If you want to go for KDE again just go to synaptic and search for kde. That should pull in all the packages needed for a KDE desktop. I always add kdm, which is the equivalent of gdm, but since it's newly installed it'll ask you which desktop environment to boot.

NOTE: I haven't done this since upgrading to Hardy from Gutsy.

---

