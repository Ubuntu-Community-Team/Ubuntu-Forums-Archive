---
title: "Apt-Get vs. Aptitude"
date: 2008-05-17
forum: Recurring Discussions
---

### Post by ghindo on 2008-05-17
Which package-management tool do you use?  Which one is better?  How are they different?

---

### Post by qazwsx on 2008-05-17
> **ghindo said:**
> Which package-management tool do you use?  Which one is better?  How are they different?
Aptitude needs apt.
You can use aptitude in TUI as well


Aptitude gives more automation.
Apt gives more control and I prefer that.

---

### Post by aheckler on 2008-05-17
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Saint Angeles on 2008-05-17
[http://ubuntuforums.org/showthread.php?p=4978484#](http://ubuntuforums.org/showthread.php?p=4978484#)

---

### Post by szymon_g on 2008-05-17
apt-get will not remember dependencies installed with a program, aptitude will remember it, and when you will uninstall it, it will uninstall its dependencies as well (of course if they arent needed by other programs).
personally, i always use aptitude.

ah, i would forgot: by default, aptitude is installing also recommends programs (i.e. programs recommends by other programs), so, by defoult, it will download and install more programs/libraries than apt-get. you may solve this 'problem' by typing

sudo aptitude --without-recommends install program_name

---

### Post by Saint Angeles on 2008-05-17
> **szymon_g said:**
> apt-get will not remember dependencies installed with a program, aptitude will remember it, and when you will uninstall it, it will uninstall its dependencies as well (of course if they arent needed by other programs).
personally, i always use aptitude.

ah, i would forgot: by default, aptitude is installing also recommends programs (i.e. programs recommends by other programs), so, by defoult, it will download and install more programs/libraries than apt-get. you may solve this 'problem' by typing

sudo aptitude --without-recommends install program_name
what about apt-get autoremove or autoclean? doesnt that remove un-needed dependencies?

---

### Post by cb951303 on 2008-05-17
isn't possible to achive the same thing with "apt-get remove FOO && apt-get autoremove" 

?

---

### Post by szymon_g on 2008-05-17
> **Saint Angeles said:**
> what about apt-get autoremove or autoclean? doesnt that remove un-needed dependencies?


hmm... i'm not on linux now, so i cannot check it... but, btw, i'd rather stick with aptitude (i'm just to lazy to run those, additional commands, if i can do it in one command ;p) it satisfy me (in most cases).
prabably man apt-get, man aptitude and man dpkg would answer your question ;)

---

### Post by bufsabre666 on 2008-05-17
> **Saint Angeles said:**
> what about apt-get autoremove or autoclean? doesnt that remove un-needed dependencies?

i might be wrong, but i always thought that autoremove just got rid of the old installer files that were no longer needed

---

### Post by cb951303 on 2008-05-17
> **bufsabre666 said:**
> i might be wrong, but i always thought that autoremove just got rid of the old installer files that were no longer needed

not at all, it removes the no longer necessary installed packages that are once installed as a dependency :) what you are talking about is "apt-get clean". Here is what man has to say about autoremove and autoclean

```

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

```
Notice that autoremove looks only for packages installed as a dep. For example if you install SDL and a game that depends on SDL separately, when you uninstall the game and run an "autoremove" SDL will stay. I don't know if that's the case with aptitude, but that's the way it should be...

---

### Post by drivel on 2008-05-17
I'm using apt-get because it's cow power.

---

### Post by bufsabre666 on 2008-05-17
> **cb951303 said:**
> not at all, it removes the no longer necessary installed packages that are once installed as a dependency :) what you are talking about is "apt-get clean". Here is what man has to say about autoremove and autoclean

```

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

```
Notice that autoremove looks only for packages installed as a dep. For example if you install SDL and a game that depends on SDL separately, when you uninstall the game and run an "autoremove" SDL will stay. I don't know if that's the case with aptitude, but that's the way it should be...

i stand corrected, man i miss apt, oh well back to yast and zypper

---

### Post by ghindo on 2008-05-17
To be honest, it doesn't sound like there's any *significant* difference between apt-get and aptitude after Ubuntu 6.10 came out.  I'm sure there are subtle nuances, but it sounds like they essentially function the same way.

---

### Post by ShodanjoDM on 2008-05-17
Aptitude, most of the time. Personally I think it still handles dependencies removal better than apt-get. Besides, the way I type "aptitude" feels more natural and convenient than apt-get.

---

### Post by Trail on 2008-05-19
aptitude search <pattern>

Winner? :) I always use that instead of gui applications. More specifically, aliases like agu, agg, ags etc.

---

### Post by barbedsaber on 2008-05-19
is this a recurring discussion?  I am no mod, but still...

---

### Post by dizee on 2008-05-19
I use apt-get. Aptitude is better with removing dependencies when you uninstall, but in my experience it was a little over-zealous a few times with what it wanted to remove. So back to apt-get (and apt-cache search) I went.

---

### Post by SunnyRabbiera on 2008-05-19
Both are quite good, apt alone is very simplistic, but I also like aptitude because of its near gui like functionality.

---

### Post by tdrusk on 2008-05-19
As far as CLI the basic user can achieve the same things with both.

---

### Post by aysiu on 2008-05-19
> **barbedsaber said:**
> is this a recurring discussion?  I am no mod, but still...
Yes, it is, so I've moved it there. In the future, you can click the REPORT button to get all the mods' attentions.

---

