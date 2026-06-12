---
title: "Keeping the system clean"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by ClaraMFerreira on 2011-11-22
Hi!
First of all, I think I might be using the wrong category, but since I have no previous knowledge on the matter and it doesn't seem like a urgent support, I thought it fitted here. :)

I don't tend to be a person who clutters the computer a lot, my personal folders always have a spring cleanup. On Windows I tended to keep the system clean and shining frequently, since I knew beyond the basics I searched for specific folders and settings, and also had the help of Ccleaner.

Here on Ubuntu I have absolutely no idea on how to do that clean, or even if it's really necessary. I searched here and there but apparently there are many solutions and in none I know what is going on exactly and if it's risky.

My question would be, in general, what's the best way of cleaning the system once in a while, while keeping everything safe. I would really like to avoid automatic scripts, if I want to learn more on Ubuntu I want to know what exactly is going on.
Any link to any tutorial or instruction can be useful too!

Thanks in advance. :)

---

### Post by ron999 on 2011-11-22
> **ClaraMFerreira said:**
> ... On Windows I tended to keep the system clean and shining frequently, since I knew beyond the basics I searched for specific folders and settings, and also had the help of **Ccleaner**.
...
My question would be, in general, what's the best way of cleaning the system once in a while, while keeping everything safe. I would really like to avoid automatic scripts,...

Hi
**BleachBit** does a similar job to CCleaner for Ubuntu.
From here --> [http://bleachbit.sourceforge.net/]("http://bleachbit.sourceforge.net/")

---

### Post by ClaraMFerreira on 2011-11-22
Now that's a nice application I didn't know of! And it has the specificity I much adore. Thanks. :)

---

### Post by collisionystm on 2011-11-22
I always heard Bleachbit is pretty powerful and to use caution with it.
I personally have never tried it.

To clean up, I guess you would just remove old PPA's and software sources
do a sudo apt-get clean to remove old downloaded files

Straighten up your home folder

uhh... i guess thats about it. There is no windows registry, not much of a temp files folder.

---

### Post by Paqman on 2011-11-22
> **ron999 said:**
> Hi
**BleachBit** does a similar job to CCleaner for Ubuntu.
From here --> [http://bleachbit.sourceforge.net/]("http://bleachbit.sourceforge.net/")

Bleachbit is actually in the repos, so just open up Ubuntu Software Centre to get it. Using your system's package manager to get software is always better than downloading it from a website, as it'll get updated automatically.

---

### Post by ajgreeny on 2011-11-22
But please don't just assume that everything listed by bleachbit is safe to remove.  If you have installed things manually from .deb installation files you may find they are included in the list, even though you want to keep them.

---

### Post by oldsoundguy on 2011-11-22
Another one to look into is Ubuntu Tweak. Removes a lot of stuff including old and outdated kernels.  But use sparingly and READ what you are doing. I usually run it after a kernel update.  That seems often enough.

One thing to understand is that Linux does not leave anything near the amount of stuff behind that Windows does.  And Linux does not have that pile of registry files left behind after you do installs and updates.

---

### Post by ubupirate on 2011-11-22
+1 for bleachbit and +1 for ubuntu tweak.

---

### Post by I2k4 on 2011-11-22
I've tried out various Ubuntu versions on Live USB before committing to a dual boot on my netbook and am still using small 4GB sticks on my main machine, so I share the interest in minimizing useless crud.  I've been using Bleachbit with success and it's now part of my routine Ubuntu software installation - I didn't have success with the "Computer Janitor" app supplied by some Ubuntu versions, since it jammed the Live USB.  

One very good thing Bleachbit does is to warn about consequences of settings during the setting tick-off process - some settings are slow, some are still in development, some remove commonly relied on features (like all your Firefox bookmarks) so it's important to be careful, but Bleachbit is pretty good about warnings to users.  I've used CCleaner on Windows for several years, and only wish it would incorporate similarly detailed warnings about what might happen if you do the purge.

---

### Post by lolpenguin on 2011-11-23
To help keep the software clean, run these every now and then:
```
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
```
autoremove removes unused packages, clean removes unused Debian packages, autoclean removes old unused Debian packages.
Also, computer janitor (computer-janitor-gtk) is available in the oneiric/universe repository. It removes unused, unsourced packages and installs required ones.

---

### Post by mörgæs on 2011-11-23
> **lolpenguin said:**
> To help keep the software clean, run these every now and then:
```
sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
```


+1

When upgrading to a new Buntu: If you do a fresh install rather than an online upgrade you will always have a clean system. No need  for a more or less risky manual clean-up.

---

### Post by OrangeCrate on 2011-11-23
Additional tips on keeping your system clean are here:

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

