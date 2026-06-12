---
title: "How to install Zukitwo Cupertino 0.5.3"
date: 2014-09-20
forum: New to Ubuntu
---

### Post by czgirb on 2014-09-20
the theme URL is as follow [http://gnome-look.org/content/show.php/?content=149412](http://gnome-look.org/content/show.php/?content=149412)
in order to install the theme, i do:
1. **extract** the theme in **Downloads** folder
2. open **TERMINAL** and type **gksudo nautilus**
3. and copied the **zukimac** and **zukimac-ml** and paste it into **usr/shares/themes**
4. but the theme was not detected, both by **Appearance** and **GNome Tweak Tool**
so i install the theme by using **Ubuntu Tweak** ... **Tweak > Themes >** and change **GTK Theme** and **Window Theme** only, other remain the same as **Radiance**.
I've tried both **zukitwo-mac** and **zukitwo-mac 3.10**, and the result is the same ... my **Top Panel** was **Blackened (Absolute Black)**.
Why ???
Even I restart the machine, my **Top Panel** was **Blackened (Absolute Black)**.
 Please guide me ...

---

### Post by Rob Sayer on 2014-09-20
This may not be what you'd want to hear but here goes:

- according to the changelog in the above link that hasn't been updated since December 2013.  Which is before ubuntu 14.04 came out.  Which means it can't be counted on at all to work in 14.04.

- I won't touch 3rd party themes with a 10 foot pole anyway.  Your DE is far to important to mess around with elements from untrusted ppa's.  It may work OK at first but there's an excellent chance it'll get borked when you do a system update.  I won't even even use 3rd party skins for app software for that reason.

- I won't use 3rd party ppa's for anything actually unless it's something I just can't do with something available in the tested ubuntu repos.  Big noob mistake IMHO.  

- I no longer read many of those linux blogs.  Some are good but many aren't even written by knowledgeable people.  I've seen some really bad advice on them.  My advice would be to stick to here and askubuntu.

I'd also yank that theme and remove the ppa from the apt sources list.

---

### Post by Frogs Hair on 2014-09-20
The link provided is for a Gnome Shell theme and there were no GTK themes included with the package when downloaded. Is the link correct and are you using the Gnome Shell which is what the theme is for ?

---

### Post by gifford on 2014-09-20
This might be what you are looking for: [http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html](http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html)

---

### Post by czgirb on 2014-09-21
> **gifford said:**
> This might be what you are looking for: [http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html](http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html)
Maybe ... but I think I rather to stick with the default theme ... as quoted below

> **Rob Sayer said:**
> This may not be what you'd want to hear but here goes:

- according to the changelog in the above link that hasn't been updated since December 2013.  Which is before ubuntu 14.04 came out.  Which means it can't be counted on at all to work in 14.04.

- I won't touch 3rd party themes with a 10 foot pole anyway.  Your DE is far to important to mess around with elements from untrusted ppa's.  It may work OK at first but there's an excellent chance it'll get borked when you do a system update.  I won't even even use 3rd party skins for app software for that reason.

- I won't use 3rd party ppa's for anything actually unless it's something I just can't do with something available in the tested ubuntu repos.  Big noob mistake IMHO.  

- I no longer read many of those linux blogs.  Some are good but many aren't even written by knowledgeable people.  I've seen some really bad advice on them.  My advice would be to stick to here and askubuntu.

I'd also yank that theme and remove the ppa from the apt sources list.
Thank you fot the advice

---

### Post by CantankRus on 2014-09-21
> **Rob Sayer said:**
> This may not be what you'd want to hear but here goes:

- according to the changelog in the above link that hasn't been updated since December 2013.  Which is before ubuntu 14.04 came out.  Which means it can't be counted on at all to work in 14.04.

- I won't touch 3rd party themes with a 10 foot pole anyway.  Your DE is far to important to mess around with elements from untrusted ppa's.  It may work OK at first but there's an excellent chance it'll get borked when you do a system update.  I won't even even use 3rd party skins for app software for that reason.

- I won't use 3rd party ppa's for anything actually unless it's something I just can't do with something available in the tested ubuntu repos.  Big noob mistake IMHO.  

- I no longer read many of those linux blogs.  Some are good but many aren't even written by knowledgeable people.  I've seen some really bad advice on them.  My advice would be to stick to here and askubuntu.

I'd also yank that theme and remove the ppa from the apt sources list.
Noobslab and webupd8 are both well known repos just for themes which I can't see causing any major problem.
It's not as if they contain upgrades to default installed themes or applications.
I find it a much easier way to try some different themes than browsing gnomelook.
Theme doesn't look right...just switch back to default and uninstall.

---

