---
title: "Some sort of useful config file with all preferences? 8.04"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Rorke on 2008-06-23
I don't know if its a contradiction in terms, or something obvious, but I was wondering if there was any useful way to preserve preferences beyond a full re-install?

I am having problems getting screen res to go back to 1200 (or anything greater than 800) and so am considering a full DVD re-install.

It took several weeks figuring out how to get flash player (rather than gnash which didn't work) and various other settings, such as running java script from Firefox 3 etc.

Is it possible to get a Ubuntu setup saved somewhere so that if you (I!) accidently toast it (with a driver load error presumably) I can re-install and one-click it all back again how it was?:popcorn:

---

### Post by aheckler on 2008-06-23
You might just back up your entire home directory and certain other files (xorg.conf, sources.list, and so forth).

---

### Post by sydbat on 2008-06-23
Do you just copy them over after reinstalling? Would that 'break' anything? Also, you list some other files "(xorg.conf, sources.list, and so forth)"...what are the "and so forth" files? Is there a list someplace (maybe a thread elsewhere on the forum)?

Thanks in advance.

---

### Post by aheckler on 2008-06-23
Stuff like xorg.conf and your sources.list I wouldn't just copy over, but if you saved everything in your home folder (including hidden files) you should just be able to drop it right in there after a fresh install and get a lot of your settings back.

Of course, if one of these settings is somehow preventing you from getting the resolution you want, perhaps a truly fresh installation is best. It may help to write down what you're doing to get Flash working so that it's faster if you have to reinstall (so you don't have to figure it out again).

---

### Post by DGortze380 on 2008-06-23
Just backup all the config files you need. I put them in a folder in my /home directory, then wrote a  simple bash script to copy the original configs to there individual locations and replace the modified ones. one command and you're settings are restored. You just need to figure out what you're changing, and make a backup before you do then add it to the script.

---

### Post by Rorke on 2008-06-23
So, does anyone have a useful script that collects the essential conf files?
I used to write bash scripts and Korn shell stuff (10 years ago), but I don't know which files are needed for the setup.

---

