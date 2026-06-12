---
title: "tulong sa X11 installing"
date: 2008-03-01
forum: Philippine Team
---

### Post by Kulaspiro on 2008-03-01
mga kababayan,
pls help,,,,i was installing compiz fusion pero along the way i think i messed my x11,d sya makita ng comp..before i could use restricted driver, for my ati radeon m200...
nakakalaro ako dati ng tremulous, pero nagun ndi na...

d ko alam if nag back up ako ng xorg conf, so can anybody help  me sa pag install ng bagong x11?  

tried using envy to install my ati driver and hopefully reconfigure my xorg ...i think d din yun umubra

pls help

---

### Post by raxso on 2008-03-01
try running this command 

sudo dpkg-reconfigure xserver-xorg

it will ask you a series of questions and will create a new xorg.conf then saka mo install yung driver ng video card mo...

ATI radeon din gamit ko and i follow this how to... [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by Kulaspiro on 2008-03-01
thanks a lot...

another  question, my comp says na i dont need restricted driver..probably dahil sa envy, nag install sya ng driver for my ati...

you know how to undo everything that was done by envy...may ati drivers b talaga supported ang ati for ubuntu....i will install it na lang manualy

thnaks

---

### Post by raxso on 2008-03-01
you can uninstall envy

sudo apt-get remove --purge envy

running the command 

sudo dpkg-reconfigure xserver-xorg

will reconfigure your xorg.conf according to your choice..

you can download the ati drivers for linux at this site [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)


have fun....

---

### Post by echo2knight on 2008-03-03
guys, i know this is off topic, but mas maganda ba restrictive driver para sa ati o yung foss driver.

sa ubuntu kasi, sabi nya "i dont need to install a restrictive driver", ganun din recommendation ng zenwalk. mas maganda ba yung foss o yung driver mismo ng ati?

am using radeon 9200 se.

thanks!!!

---

### Post by loell on 2008-03-03
actually they already offered the ati driver as gpl or gpl compatible license for a little while now.

---

