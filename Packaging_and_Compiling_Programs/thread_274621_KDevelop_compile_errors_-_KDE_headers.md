---
title: "KDevelop compile errors - KDE headers"
date: 2006-10-10
forum: Packaging and Compiling Programs
---

### Post by Jamhos on 2006-10-10
Hey

I'm running Kubuntu (the latest one, I suppose :P), and I tried to make my first "Hello World" program in KDevelop. But after I did *Run --> Compile*, I got an error saying:

[I]checking for KDE...
configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix![/I]

I looked around a bit on the forums and other sites, and gathered that I needed the package *kdebase-dev*, but when I tried to install it using Adept, it said it would break stuff (it actually seems, reading the description, that this should be installed already, but my system is running fine without it, so yeah!).

Anyway, to discover what exactly what was causing the thing to break, I clicked on "Details", and it gave me a list of packages it would install when installing *kdebase-dev* (dependencies, I guess). I found that it was one of the dependencies that was actually causing the break - *kdelibs4-dev*.

So again, I found which dependency was causing the problem, and it turned out to be *libarts1-dev*, which in turn was having it's problem caused by *libartsc0-dev*. Turns out that *libartsc0-dev* is the one screwing everything up, but I have no idea why. I am thinking this would solve the problem, but if it doesn't, at least I might have learnt something! (That's the thing I love most about Ubuntu!).

Any help would be greatly appreciated! Thanks

---

### Post by wieman01 on 2006-10-10
Curious... Are you or are you NOT able to install "kdebase-dev" because that's certainly what you need to do if you are running KDE & want to compile stuff. So have I.

---

### Post by hey_ian on 2006-10-10
kdelibs4 is only a dummy package for kdelibs, it was added for compability with versions of KDE coming in the feature (KDE4).
This should work: In the console use sudo and type following:

```
sudo apt-get install kdebase-dev
sudo apt-get install kdelibs-dev
sudo apt-get install kde-devel
```

This should work. Do not forget to make an update before.

---

### Post by ckpyn on 2009-03-30
> **hey_ian said:**
> kdelibs4 is only a dummy package for kdelibs, it was added for compability with versions of KDE coming in the feature (KDE4).
This should work: In the console use sudo and type following:

```
sudo apt-get install kdebase-dev
sudo apt-get install kdelibs-dev
sudo apt-get install kde-devel
```

This should work. Do not forget to make an update before.

I install the 3 libs in order,but kdevelop still report err message:

configure: error:
in the prefix, you've chosen, are no KDE libraries installed. This will fail.
So, check this please and use another prefix!
checking for KDE... 
*** Exited with status: 1 ***

Then I sudo the second lib and get follow:
&#20849;&#21319;&#32423;&#20102; 0 &#20010;&#36719;&#20214;&#21253;&#65292;&#26032;&#23433;&#35013;&#20102; 1 &#20010;&#36719;&#20214;&#21253;&#65292;&#35201;&#21368;&#36733; 7 &#20010;&#36719;&#20214;&#21253;&#65292;&#26377; 0 &#20010;&#36719;&#20214;&#26410;&#34987;&#21319;&#32423;&#12290;
&#38656;&#35201;&#19979;&#36733; 1404kB &#30340;&#36719;&#20214;&#21253;&#12290;
&#35299;&#21387;&#32553;&#21518;&#23558;&#20250;&#31354;&#20986; 8712kB &#30340;&#31354;&#38388;&#12290;
&#24744;&#24076;&#26395;&#32487;&#32493;&#25191;&#34892;&#21527;&#65311;[Y/n]n
&#20013;&#27490;&#25191;&#34892;&#12290;
:confused:

---

