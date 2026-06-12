---
title: "[SOLVED] window borders gone.. darn it"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by epidemiks on 2008-08-16
I just rebooted to test StartUp-Manager, and now my window borders are gone.. emerald --replace doesn't help.. thats the extent of my troubleshooting knowledge.. help??

---

### Post by overdrank on 2008-08-16
> **epidemiks said:**
> I just rebooted to test StartUp-Manager, and now my window borders are gone.. emerald --replace doesn't help.. thats the extent of my troubleshooting knowledge.. help??

HI and have you checked the advance desktop effects and make sure the window decoration is checked.

---

### Post by jamespi on 2008-08-16
do you have an nvidia graphics card? cos i had this happen to me in feisty when they introduced compiz

try turning off desktop effects system -> preferences -> appearance -> visual effects tab <none>

if that fixes it, it might be the same problem i had, a problem with xorg.conf where the config for you grpahics card isnt set right

see this thread [http://ubuntuforums.org/showthread.php?t=889881&highlight=addargbglxvisuals](http://ubuntuforums.org/showthread.php?t=889881&highlight=addargbglxvisuals)

the bottom of the page has the solution

---

### Post by epidemiks on 2008-08-16
Overdrank, yes window decoration is checked, and all other compiz stuff is a-ok, just no borders.. oh and the terminal is a black white box

---

### Post by epidemiks on 2008-08-16
jamespi, setting effects off returns regular borders.

I don't recall messing with the nvidia settings before the reboot, and it had been working fine for several days since last change

---

### Post by epidemiks on 2008-08-16
> **jamespi said:**
> do you have an nvidia graphics card? cos i had this happen to me in feisty when they introduced compiz

try turning off desktop effects system -> preferences -> appearance -> visual effects tab <none>

if that fixes it, it might be the same problem i had, a problem with xorg.conf where the config for you grpahics card isnt set right

see this thread [http://ubuntuforums.org/showthread.php?t=889881&highlight=addargbglxvisuals](http://ubuntuforums.org/showthread.php?t=889881&highlight=addargbglxvisuals)

the bottom of the page has the solution


mate! that did it.. cheers muchly

---

