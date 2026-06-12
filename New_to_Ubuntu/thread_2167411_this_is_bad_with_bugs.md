---
title: "this is bad with bugs"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by dave6 on 2013-08-13
OH dear, what a mess, done by that hacker, I never got my first log-in name sorted, now after a few weeks  try to re-log in as the new me, can't get in so I reset myself up as a new user, guess what, the system has put me back in again as dave6, the old, new me............

Any way, bug or not, 
PrtScn do't work with ubuntu 12.04lts, works OK with xp and 7 on the same computer key-brd set up

PDF files header's are cut off, when I try to print them off for the TAX man, that in itself, would be OK except the header contains name log payee number.

Lack of spell checker UK

Final bit, how do I upgrade gimp 2.6 to 2.8, as that may be the problem with not print screen

Thanks

dave6 or DaveMcC

I am now confussed, as how I am ever going to re-log in

---

### Post by GwL3eNC on 2013-08-13
Hi,

you can use this ppa [https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp) for upgrade, or you must compile
the source code manualy.

---

### Post by ajgreeny on 2013-08-13
> **dave6 said:**
> 
1) PrtScn do't work with ubuntu 12.04lts, works OK with xp and 7 on the same computer key-brd set up

2) PDF files header's are cut off, when I try to print them off for the TAX man, that in itself, would be OK except the header contains name log payee number.

3) Lack of spell checker UK

4) Final bit, how do I upgrade gimp 2.6 to 2.8, as that may be the problem with not print screen
  

1)PrtScn should work for you in 12.04 and does in my system, so I presume either your hardware must be the problem or there is some glitch in your installation.  Have you looked in the keyboard shortcut listing dialog to see if it is enabled?  Did you do a clean install or upgrade from a previous version?

2) When I print pdf files I always check in the print preview first and set the scaling to the best for the page to be printed, otherwise I sometimes have the same problem as you are seeing.  Give it a try to see if that also helps you.

3) What application do you want a spellchecker for?  Usually all you need to do is install the appropriate locale of aspell, hunspell and/or myspell.  I have all three and get spellcheckers in Libreoffice, thunderbird, abiword, etc etc.

4) For gimp 2.8 go with that ppa repository; it work beautifully and I think 2.8 is much better than 2.6, in particular the single window mode, now that I have a widescreen monitor.

---

### Post by dave6 on 2013-08-13
> **GwL3eNC said:**
> Hi,

you can use this ppa [https://launchpad.net/~otto-kesselgulasch/+archive/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/gimp) for upgrade, or you must compile
the source code manualy.

looked at that, no idea what it is, or what to do with it, sorry, that ain't any good to me

Dave

> **ajgreeny said:**
> 1)PrtScn should work for you in 12.04 and does in my system, so I presume either your hardware must be the problem or there is some glitch in your installation.  Have you looked in the keyboard shortcut listing dialog to see if it is enabled?  Did you do a clean install or upgrade from a previous version? 
keyboard shortcut listing dialog to see if it is enabled? And,,, where might they be hiding at ?
Clean install from ver 10.10


> **ajgreeny said:**
> 1)
2) When I print pdf files I always check in the print preview first and set the scaling to the best for the page to be printed, otherwise I sometimes have the same problem as you are seeing.  Give it a try to see if that also helps you. 
Print previw is 100%, just can not get the dam thing down the page

> **ajgreeny said:**
> 1)
3) What application do you want a spellchecker for?  Usually all you need to do is install the appropriate locale of aspell, hunspell and/or myspell.  I have all three and get spellcheckers in Libreoffice, thunderbird, abiword, etc etc. 
spellchecker for?,,, here, this, don't use any of the other things you have named

> **ajgreeny said:**
> 1)
4) For gimp 2.8 go with that ppa repository; it work beautifully and I think 2.8 is much better than 2.6, in particular the single window mode, now that I have a widescreen monitor.
ya, 2.8 comes stnadard with lubuntu 12 lts, yes single window mode is good, + a few wee other things that have been improved, as my computers are used 95% for photo's, No before you ask for think, I o NOT have or want photoshop
Dave

---

### Post by Hylas de Niall on 2013-08-14
> **dave6 said:**
> keyboard shortcut listing dialog to see if it is enabled? And,,, where might they be hiding at ?
spellchecker for?,,, here, this, don't use any of the other things you have named

ya, 2.8 comes stnadard with lubuntu 12 lts, yes single window mode is good, + a few wee other things that have been improved, as my computers are used 95% for photo's, No before you ask for think, I o NOT have or want photoshop
Dave

You mean a spellchecker for your browser? Which browser are you using and is a spellchecker included in that somewhere, or available as an add-on? ...not an Ubuntu issue. Nor is it a bug. :(

Gimp 2.8 most emphatically does *NOT* come as standard in Lubuntu 12(.04?)(LTS?). _No_ version of Gimp is included by default, but you can install v2.6 from the repositories.

[https://www.youtube.com/watch?v=yanEoPznXAc](https://www.youtube.com/watch?v=yanEoPznXAc)

You might mean 'LXLE' which is an independent side project running an enhanced version of Lubuntu desktop on top of Ubuntu 12.04 for which the PPA's are already set up for things such as Gimp 2.8 and the Deepin Software Centre. That is a great distro, but it is not Lubuntu 12.04.

[http://www.lxle.net/](http://www.lxle.net/)

As for using a PPA to get the latest Gimp, a little googling would give you the answer you require:

[http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu](http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu)

HTH

---

### Post by mastablasta on 2013-08-14
PPA - basically you ad a ppa to software sources in software center, refresh the software center and then search for gimp. you should see the 2.8 ption available then... anyway the isntrucitons on how to do it in command line are on the launchpad site. copy and paste those commands...

---

### Post by dave6 on 2013-08-14
> **mastablasta said:**
> PPA - basically you ad a ppa to software sources in software center, refresh the software center and then search for gimp. you should see the 2.8 ption available then... anyway the isntrucitons on how to do it in command line are on the launchpad site. copy and paste those commands...

Hi mastablasta, ):P you helped me before "big time" on getting ubuntu to look and feel the way I like, 
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

Which may "be" now my un-doing ???? :confused: don't know, back before the hackers hit, there was a search part thing, but it seems to be away

was there not a thing like > sudo upgrade-get gimp 2.8 sudo install gimp 2.8 < I am only guessing as I don't have a clue about command codes don't want to either

Dave

---

### Post by zombifier25 on 2013-08-14
GIMP 2.8 was not included in Precise, and if you want it, you need to add a PPA, basically an extra repository for Ubuntu which contains GIMP 2.8. Simply run these commands to install the PPA and GIMP 2.8:
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get purge gimp
sudo apt-get install gimp
```

Some people said that if you don't purge 2.6 before installing 2.8, there might be problems, so I included the "purge" line.

EDIT: If you want the graphical way, then open "Software Sources", go to the  "Other Software" tabs, click "Add", then insert ```
ppa:otto-kesselgulasch/gimp
``` into the box. Then exit, update the cache as prompted, then upgrade GIMP.

---

### Post by Hylas de Niall on 2013-08-14
> **dave6 said:**
> The one that comes with ubuntu, ? why ! is there more than one, that loads now with ubuntu on install ???

After I installed lubuntu on other computer, I clicked on "install gimp" 2.8 loaded by default, ON ubuntu 12.04 lts when I done the same action, 2.6 loaded, which I want to upgrade to 2.8, as clearly stated in my first post, person from england, you may have to learn to read............

All these words with no meaning to me, so here is one for you, great tails to be had, SSE from the IE sector on the green lane

If I had wanted to waste my life googling, like a lot of other sad acts "social media" I would not have asked here on the fourm's** ABSOLUTE BEGINNERS SECTION** nuf said

As you seem to have taken offense for some reason i'll keep it short and sweet. :)

1. Many other browsers are available in the software centre and a lot of folk choose to use them instead, you didn't indicate which one you used so i asked. Is that hard to fathom?

2. Applications in Lubuntu:   [https://help.ubuntu.com/community/Lubuntu/Setup#Applications](https://help.ubuntu.com/community/Lubuntu/Setup#Applications) 
You clearly stated version 12.?? which only holds version 2.6 Gimp in the repos that is what i said. Lubu *13.04* can install version 2.8 Gimp.

3. So it's not LXLE then [http://www.lxle.net/](http://www.lxle.net/)

4. Google is a search engine that millions use to find out stuff, not a 'sad acts "social media"'.

HTH (hope that helps)

Have a good one :)

One question; are you using Ubuntu or Lubuntu? Your posts seem to say one then the other.

---

### Post by dave6 on 2013-08-14
> **zombifier25 said:**
> GIMP 2.8 was not included in Precise, and if you want it, you need to add a PPA, basically an extra repository for Ubuntu which contains GIMP 2.8. Simply run these commands to install the PPA and GIMP 2.8:
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get purge gimp
sudo apt-get install gimp
```

Some people said that if you don't purge 2.6 before installing 2.8, there might be problems, so I included the "purge" line.

EDIT: If you want the graphical way, then open "Software Sources", go to the  "Other Software" tabs, click "Add", then insert ```
ppa:otto-kesselgulasch/gimp
``` into the box. Then exit, update the cache as prompted, then upgrade GIMP.

Thanks zombifier25 for the coding, that got the gimp into the system, now both computers here, have the same version of gimp

Computer 2 Lubuntu version 12.10 
Computer 1 Ubuntu Release 12.04 (precise) 64-bit, Kernel Linux 3.2.0-49-generic, GNOME 3.4.2, with out the bar down the left hand side, that is why I don't have "Software Sources",  "Other Software" tabs, "Add",
Won't bother about the spell chceker, as long as I know what I am writing, my version of ubuntu coding

Dave

---

