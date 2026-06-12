---
title: "HELP. I'm Pulling out all my hair trying to remove software HELP ANYONE"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by SteveMHaupt on 2012-01-12
I'm trying to remove Avast virus scan in installed from a deb package using dpkg -i avast4workstation_1.3.0-2_i386.deb. I'm not happy with it and choose to remove it. Easier said than done I soon learned. I tried dpkg -r avast4workstation_1.3.0-2_i386.deb and was told i need to specify a specific name and not the package it came in. I'm have trouble locating the name of the file i need to use to uninstall the dam thing. Perhaps I'm entering the commandc wrong. I've looked in the usr/bin and find nothing having anything to do with avast not even any dot files. What am I doing wrong. PLEASE some one save me with your signifigantly vast knowledge to a newbie who is teetering on the brink of Ubuntu Suicide. 
Thanks Steveo

---

### Post by Krytarik on 2012-01-12
This command should do it - notice, name of the package needed, not the name of the file you installed it from initially:
```
sudo apt-get purge avast4workstation
```Or if you prefer to stick with "dpkg" ;-) :
```
sudo dpkg --purge avast4workstation
```Regards.

---

### Post by dcsoldschool53 on 2012-01-12
If by chance, you have the program synaptic package manager installed on your system, you can also use it to UN-install avast.

---

### Post by |{urse on 2012-01-12
Huh,purge

Ive always used sudo apt-get remove program

Is purge better?  Amidoinitwrong?

>  I'm have trouble locating the name of the file i need to use to uninstall the dam thing

Haha, yeah, fun. Next time try apt-cache search.

Lets say I installed Tremulous which is a first person shooter, and needed to find the name of the package to remove to uninstall it.. 

> apt-cache search shooter

With the given results I can find the name of the package quickly.

---

### Post by Krytarik on 2012-01-12
> **|{urse said:**
> Huh,purge

Ive always used sudo apt-get remove program

Is purge better?  Amidoinitwrong?
:D Not really, usually only wasting some space. If you want to remove a package completely without having leftovers, use "purge".
> **remove**
    remove is identical to install except that packages are removed
    instead of installed. Note the removing a package leaves its
    configuration files in system. If a plus sign is appended to the
    package name (with no intervening space), the identified package
    will be installed instead of removed.

**purge**
    purge is identical to remove except that packages are removed and
    purged (any configuration files are deleted too).[http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/oneiric/en/man8/apt-get.8.html)

Notice: "configuration files" doesn't mean config files in your home directory, like often mistaken!

---

### Post by SteveMHaupt on 2012-01-12
Thanks for the help. Worked like a charm and also cleared up a real grey area as far as software install and removal goes. I'm using ubuntu 11.10 and after I initially installed Avast, the ubuntu software center didn't recognize it. I know that sometimes if you double click a deb file from inside Gnome or Unity it will install that way(which I never use, Trying to do everything possible from the command line). but Avast wasn't there to unistall. Doesnt really matter. If I wanted a fruity Gui to help me do everything I would go back to windows and I aints gonna do that. DOWN WITH MICROSOFT. Thanks again. Literally spent all day trying to figure it out on my own. Sometimes you just have to have it broken down kindergarten style.

---

