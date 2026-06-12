---
title: "Libreaoffice spell checker"
date: 2018-04-22
forum: New to Ubuntu
---

### Post by dave1956 on 2018-04-22
Hi guys.  I have discovered that the spell checker in office either does not work or there is none install.

If it is not part of office on a fresh upgrade (that when horribly wrong ) how do I install it.  

Dave

---

### Post by Dennis N on 2018-04-22
Check in Tools > Options > Language Settings > Languages.
Is the default language for Documents set correctly?
Check in Tools > Options > Language Settings > Writing Aids.
Is there a spell checker listed and enabled in "Available Language Modules"? It is called Hunspell SpellChecker. 
If you want to check while typing, be sure that option is checked.

---

### Post by dave1956 on 2018-04-22
Thanks Dennis N
I have done all that and yes just as you written every thing checked etc.
You  will note that I wrote Libreoffice wrong, I have added an A to it, when testing the spell checker in libreoffice it does not try to correct it or inform me of the mis-spell
Strange ?
Dave

Just checked the following.
options  Libreoffice - Paths
Dictionaries  /home/me/.config/libreoffice4/user/wordbook

---

### Post by Dennis N on 2018-04-22
F7 should cause a check and bring up an actions dialog whether you have it set to check while typing or not. That doesn't work? See screen shot attached.

My system: I am using Ubuntu 17.10 - L.O. was installed as a default application.

---

### Post by dave1956 on 2018-04-24
And this is what I get when I run the checker.. Must add, that I have had a load of problems using Ubuntu16.04 which was an upgrade from Ubuntu 12
In the next couple of weeks I am going to give it a clean install with Ubuntu Mate 18.04

---

### Post by sevendogsbsd on 2018-04-24
Make sure the packages "hunspell" and "hunspell-en-us" are installed. If that's your language...I have a clean install of 18.04 beta 2 and neither package was installed by default, if I remember correctly.

---

