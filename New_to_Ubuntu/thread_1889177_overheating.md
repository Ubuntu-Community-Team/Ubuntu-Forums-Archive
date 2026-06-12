---
title: "overheating"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by Oxyris on 2011-11-30
Straight to the point:
laptop runs hotter under ubuntu than windows. I'm now dual booted but before I was using wubi and I had the same problem (didn't care to fix it as wubi was just temporary). I guess it has to do with the fact my laptop has nvidia optimus but before I try to do the bumblebee thing (which looks complicated for a noob like me) is it reasonable to expect the laptop to run less hot? I don't really want to go around fixing what ain't completely broke.

---

### Post by bluexrider on 2011-11-30
NO mention of what distro you are running so assuming here: 11.04 and 11.10 have had kernel issues ranging from overheating to lower than expected battery times. 

Dont know anything about nvidia optimus being an issue but who knows

Specific questions=specific answers what can the forum help you with?

---

### Post by creator101 on 2011-11-30
Get a cooling pad!:lolflag:

---

### Post by 001neeraj on 2011-12-01
You can install the package 'Thinkfan' which can be used to control your fan. It will help you upto a  limit. Also install the package 'Jupiter'. Jupiter used to control performance modes. You have to add repositories for installing Jupiter. Use Google for to find it.

---

### Post by LewisKolb on 2011-12-01
thats qeird, ubuntu is alot less resource intensive than windows, update your drivers / roll em back, see what happens.

---

### Post by Mark Phelps on 2011-12-01
> **LewisKolb said:**
> thats qeird, ubuntu is alot less resource intensive than windows, update your drivers / roll em back, see what happens.
This is a BUG in the latest kernel versions.

It's NOT a driver problem, it has nothing to do with resource usage.

---

### Post by blade4 on 2011-12-01
Like the good folks said - its a bug in ubuntu and not a problem with your hardware . Nevertheless , here are some tips to reduce heating :

1) Try enabling laptop mode . You might have to download it from synaptic ( just search laptop-mode-tools ) and configure it - the instructions are in its manual and on google . 

2) Go to [http://www.lesswatts.org/tips/](http://www.lesswatts.org/tips/)  for more tips on reducing power consumption .  

3) Try to open up your laptop a bit - take out the remote and the dvd reader if the laptop allows it .

Bear in mind that the first two tweaks are a bit advanced and will affect your performance if you put in the wrong settings . But if you are really concerned about the heating problem , give 'em a try . 

Side note : you can check your drive temp by typing "sensors" ( minus quotes) in terminal .

---

### Post by shuttleworthwannabe on 2011-12-01
No to rain on your parade here, but this is the primary reason I have not installed a Linux Distro on my laptop. They all run hotter and fan just keeps blowing in Linux (any flavor).

Until this is fixed, it is a risk to install then expect the novice to figure it out how to "fix" it in the interim.

Pity.

---

