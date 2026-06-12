---
title: "install and run wine on ubuntu 9.04"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by Hankbonk on 2013-11-06
I'm getting an error when I try to instaal wine in ubuntu 9.04 :

root@henk-desktop:/# apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

And I did edit the sources.list with the two needed lines !
Can anybody help me out ?

---

### Post by DuckHook on 2013-11-06
Running a dead-and-buried version like 9.04 is not good, and running WINE on top of it makes you a sitting duck. Last but not least, activating the root account is not good either.

I've skimmed back through your old threads and I suspect that almost all of your problems would go away if you just burned a DVD or USB of an up-to-date version like 12.04.3 and ran/installed that instead. Currently, you are confined to archive repositories, can't get updates (they're not just for security--they also squash bugs that may be plaguing you), and have largely cut yourself off from help because most of us can't remember back that far (2009 is equivalent of 40 years ago in IT time). You are making this far harder on yourself than you have to.

We have no idea what your HW is. You may wish to list it if you want effective advice. Given the data vacuum, I would suggest Xubuntu 12.04. Wine would then be available from a current and maintained repo. So would everything else that you've recently twisted yourself into knots trying to install.

---

### Post by inclusivedisjunction on 2013-11-06
Did you run apt-get update after modifying your sources list? You need to run apt-get update to fetch the list of packages from the "new" repositories you added.

---

### Post by Bucky Ball on 2013-11-06
> **DuckHook said:**
> Running a dead-and-buried version like 9.04 is not good, and running WINE on top of it makes you a sitting duck. Last but not least, activating the root account is not good either.



This and, while reasonable on a supported system, not this in your situation:

> **inclusivedisjunction said:**
> Did you run apt-get update after modifying your sources list? You need to run apt-get update to fetch the list of packages from the "new" repositories you added.

No point. 9.04 repositories no longer exist. Install a supported release. 9.04 expired in October of 2010 and you are a galaxy behind. The further behind you get the less chance of fixing problems, and yes, as far as security goes you are well vulnerable, especially chucking Wine in, if that is possible.

As you appear to like sticking with a release for a long time, I suggest 12.04 LTS, stable and supported until April 2017.

---

### Post by deadflowr on 2013-11-07
> **Hankbonk said:**
> 

And I did edit the sources.list with the two needed lines !
Can anybody help me out ?

Though I wholeheartedly agreed with Duckhook and Bucky Ball that an upgrade to a supported release is the easiest road.

My curiosity got the better of me and wonders what two lines you were suppose to add/edit?

---

### Post by Bucky Ball on 2013-11-07
> **deadflowr said:**
> My curiosity got the better of me and wonders what two lines you were suppose to add/edit?

+1. Pray tell ...

---

