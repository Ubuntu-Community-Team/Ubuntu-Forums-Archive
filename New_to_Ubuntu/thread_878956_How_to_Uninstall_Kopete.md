---
title: "How to Uninstall Kopete"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by trublu1217 on 2008-08-03
Hi! I tried installing Kopete in Ubuntu 8.04. I just switched to Ubuntu a week ago. It worked at first, I configured an account for yahoo. After adding another account, I can't see the contacts list anymore. I already tried removing and recreating the accounts. I tried to reinstall kopete but the settings are still there after installing again. Please help!

---

### Post by Elfy on 2008-08-03
You're settings are saved in a hidden folder in your home folder

Open nautilus and do Ctrl+H to view hidden files, find the kopete folder and delete it - when you run kopete again it should start from scratch

---

### Post by kirsis on 2008-08-03
FYI purging a package removes its config files too.

Like this:

sudo aptitude purge kopete

---

### Post by Elfy on 2008-08-03
Doesn't remove folders from /home though afaik - at least it doesn't for me.

---

### Post by kirsis on 2008-08-03
My bad. aptitude --help reports that

"purge        - Remove packages and their configuration files"

but when I tried it out (purged pidgin) it didn't remove any configs.

Sorry for the misinformation.

(btw, amusing sig. If that's real... ouch :))

---

### Post by Elfy on 2008-08-03
I originally thought that aptitude purge did that - but I think that it must relate to the configs that can be left behind by an apt-get remove - residual configuration in synaptic - the settings or whatever they are in /home get left by everything it seems.

The sig is very real - someone had an unrelated problem and couldn't remember what got installed last, I asked what synaptic history showed and got the "I installed it all" - I roflmao and when I'd stopped - did it all over again

---

### Post by trublu1217 on 2008-08-03
HI Forestpixie. Thanks for the assistance. I already did what you told me but I can't find the Kopete folder in home directory.

---

### Post by kirsis on 2008-08-03
It's hidden. Try pressing CTRL+H in Nautilus (or 'ls -a' in CLI)

---

### Post by trublu1217 on 2008-08-03
Thanks for the quick response Kirsis. I already did CTRL+H. It showed the hidden folders but still no Kopete folder :(

---

### Post by trublu1217 on 2008-08-03
The problem I'm having with Kopete is that my contact list in Yahoo does not appear in the main window. Maybe someone here has a solution for that so i won't need to uninstall Kopete. Thanks!

---

### Post by kirsis on 2008-08-03
Alright, I installed Kopete, checked it out...

To get rid of the old prefs, you need to:

rm ~/.kde/share/config/kopeterc

Adjust accordingly, if you have the KDE4 version :)

---

### Post by trublu1217 on 2008-08-03
Thanx Krisis. Found it. :)

---

