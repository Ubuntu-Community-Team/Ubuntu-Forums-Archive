---
title: "Session selection menu missing from login screen"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MatCat58 on 2011-10-09
I've looked everywhere I can think of online and haven't found anything posted about this bug. 

I upgraded through the update manager from ultimate edition 2.9 11.04 to 11.10 and now my session always starts as XFCE. Gnome-shell, gnome-session-fallback, and unity, as well as kubuntu-desktop have all been purged and reinstalled and are still not showing up as login options. 

Is there a way to get my session selection menu back on the login screen without doing a clean install?

---

### Post by ronacc on 2011-10-09
try going to synaptic and reloading the repos and see what pops up as upgradeable , update manager only updates/upgrades default stuff.

---

### Post by MatCat58 on 2011-10-09
> **ronacc said:**
> try going to synaptic and reloading the repos and see what pops up as upgradeable , update manager only updates/upgrades default stuff.

I typically run upgrades in the terminal almost daily so there is nothing in the upgradeable menu showing on synaptic.....

---

### Post by ronacc on 2011-10-09
I checked both my unity install and my GS install and both have the session choices , do you know what de you have , gdm or lightdm ? they switched from gdm to lightdm a couple of weeks ago that may have something to do with it .

---

### Post by MatCat58 on 2011-10-10
> **ronacc said:**
> I checked both my unity install and my GS install and both have the session choices , do you know what de you have , gdm or lightdm ? they switched from gdm to lightdm a couple of weeks ago that may have something to do with it .

Ok now it's getting really weird. I had both lightdm and gdm installed. I purged gdm and restarted light to no effect. I then reinstalled gdm in a tty and seet it as the primary dm. I stopped lightdm and started gdm and now I have all my session selections at the login screen and can start a gnome session as well as kde and others.

---

### Post by LinuxFan999 on 2011-10-10
Just simply remove XFCE.

---

### Post by ronacc on 2011-10-10
> **MatCat58 said:**
> Ok now it's getting really weird. I had both lightdm and gdm installed. I purged gdm and restarted light to no effect. I then reinstalled gdm in a tty and seet it as the primary dm. I stopped lightdm and started gdm and now I have all my session selections at the login screen and can start a gnome session as well as kde and others.

yeah not everything plays nice with lightdm yet , lots of complaints about problems , I'm not sure that such a big change midway through the cycle was a good idea .

---

### Post by MAFoElffen on 2011-10-10
> **ronacc said:**
> yeah not everything plays nice with lightdm yet , lots of complaints about problems , I'm not sure that such a big change midway through the cycle was a good idea .
For me... Lightdm didn't work out for me (tried every day and ended back with GDM) ...until about a week and a half ago... Now lightdn seems to work fine for mine here. At least so far today, it show unity, unity 2D, Gnome, etc.

---

