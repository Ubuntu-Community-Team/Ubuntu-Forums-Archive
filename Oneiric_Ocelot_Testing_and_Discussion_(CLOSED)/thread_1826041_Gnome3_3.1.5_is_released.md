---
title: "Gnome3 3.1.5 is released"
date: 2011-08-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-16
The new 3.1.5 version of Gnome3 is arriving into Oneiric repos.
The first packages there already are
- eog
- gconf
- gnome-desktop3
- gnome-session
- gnome-settings-daemon (dependency wait on libcolord-dev)

The next phase will then be 3.1.90 (beta) later in August and 3.1.92 (rc) in early September, before the final release 3.2 in late September.

---

### Post by Quackers on 2011-08-16
Luvverly :-)  Thanks Harry33.

---

### Post by shuttleworthwannabe on 2011-08-16
Does it come with settings to change the fonts and appearance by default? if not then it is a humongous FAIL--I am not talking about installing (additionally) the gnome-tweak-tool app after the fact. How would a previous Gnome 2 user even know this?

Many threads to this effect--1 right [here]("http://ubuntuforums.org/showthread.php?t=1825445").

---

### Post by sgage on 2011-08-16
> **shuttleworthwannabe said:**
> Does it come with settings to change the fonts and appearance by default? if not then it is a humongous FAIL--I am not talking about installing (additionally) the gnome-tweak-tool app after the fact. How would a previous Gnome 2 user even know this?

Relax, it's Alpha software. :KS

---

### Post by walt.smith1960 on 2011-08-16
> **sgage said:**
> Relax, it's Alpha software. :KS

Precisely.  Gnome-Shell on Ubuntu is well ahead of where it was a month or 6 weeks ago.  I find it (gnome-shell) quite usable .  I'll bet by the time it has 10 years development like Gnome 2 has had, it'll be pretty good.  I think Canonical may have chosen a pretty good course here.  The way I understand it, Gnome shell has a framework for add-ons so indicator-app and eye candy developers can go nutzz.  Unity is more for the "I don't care about the latest ever-changing  glittering revolving crap.  I just want to learn one desktop and have it work"  crowd.  It's a challenge to keep both camps happy while on a budget.

---

### Post by Sennaista on 2011-08-16
So any new functionality?

---

### Post by Harry33 on 2011-08-16
Gnome3 v. 3.1.5 has all the main functions the Gnome3.2 will have.
You see there is the Feature Freeze now (new functionality is already chosen).

---

### Post by Sennaista on 2011-08-16
Ok.

---

### Post by tad1073 on 2011-08-16
Gnome-Shell blows Unity out of the water!!!

---

### Post by jbicha on 2011-08-16
> **shuttleworthwannabe said:**
> Does it come with settings to change the fonts and appearance by default? if not then it is a humongous FAIL--I am not talking about installing (additionally) the gnome-tweak-tool app after the fact. How would a previous Gnome 2 user even know this?

Sorry that's a GNOME decision. For better or for worse, open source software development decisions are made by the ones who actually do the development. There are very few GNOME 3 themes anyway (Ambiance & Radiance don't fully work with Gnome Shell) so there's not much to choose between.

gnome-tweak-tool is a great app. Since it's written in Python, it's reasonably easy for people to contribute to and make it better.

---

### Post by Sennaista on 2011-08-16
Either some of these features didn't make it or they are somehow hidden given the code is already in feature freeze. 

[http://www.webupd8.org/2011/07/expected-changes-in-gnome-shell-32.html](http://www.webupd8.org/2011/07/expected-changes-in-gnome-shell-32.html)

---

### Post by dext on 2011-08-17
they all maybe in the beta, not the 3.1.5

---

### Post by bash on 2011-08-17
> **Sennaista said:**
> Either some of these features didn't make it or they are somehow hidden given the code is already in feature freeze. 

[http://www.webupd8.org/2011/07/expected-changes-in-gnome-shell-32.html](http://www.webupd8.org/2011/07/expected-changes-in-gnome-shell-32.html)

At least in respect to GNOME-Shell we are still stuck on version 3.1.3. Even Ricotz Testing PPA hasn't updated it's Shell package since July 18th. So quite possible that some of those features were added to the Shell in .1.4 or .1.5

---

### Post by Harry33 on 2011-08-17
> **bash said:**
> At least in respect to GNOME-Shell we are still stuck on version 3.1.3. Even Ricotz Testing PPA hasn't updated it's Shell package since July 18th. So quite possible that some of those features were added to the Shell in .1.4 or .1.5

Ricotz Staging PPA has Gnome-shell 3.1.4 git version updated today + a number of other related packages.
These all work well ATM.

---

### Post by sgage on 2011-08-17
> **Harry33 said:**
> Ricotz Staging PPA has Gnome-shell 3.1.4 git version updated today + a number of other related packages.
These all work well ATM.

Not for me - all I get is a desktop, no panel or activities.

Any idea when GS 3.1.5 will hit the official repos?

---

### Post by Harry33 on 2011-08-17
> **sgage said:**
> Not for me - all I get is a desktop, no panel or activities.

Any idea when GS 3.1.5 will hit the official repos?

Well I am afraid not very soon.

The package gnome-shell just got updated, to the version 3.1.3-0ubuntu4.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.3-0ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.3-0ubuntu4)

That update will cause troubles. A dependency wait.
First of all, it does not depend on the current libgjs0b, but instead, libgjs0c.

A new gjs package has been built, but it is not in repos yet.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gjs/1.29.16-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/gjs/1.29.16-0ubuntu2)

Note, that you can install that one only with the gnome-shell_3.1.3-0ubuntu4,
which is in a dependency wait now.

Anyway, more problems:
The latest gnome3 theme just got updated too (gnome-themes-standard_3.1.5-0ubuntu1).
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-themes-standard/3.1.5-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-themes-standard/3.1.5-0ubuntu1)

That, for a surprise, will break the whole theming system with the current gnome-shell_3.1.3-0ubuntu3, leaving you without any theme.

So do not update the gnome-theme-standard, if you are using gnome-shell with the default theming.
Do not update gnome-shell nor gjs either, until this is clear.

---

### Post by bash on 2011-08-17
> **Harry33 said:**
> Ricotz Staging PPA has Gnome-shell 3.1.4 git version updated today + a number of other related packages.
These all work well ATM.

Thanks for the heads up. Was still using the good old testing PPA which still has 3.1.3 git. Switched to staging now.

Since afaik Oneiric will ship with GNOME 3.2 final, I hope that they'll update the Shell version to 3.2 as well for the release. Else why it would make for kind of a broken experience.

---

### Post by jbicha on 2011-08-17
> **Harry33 said:**
> Well I am afraid not very soon.

The package gnome-shell just got updated, to the version 3.1.3-0ubuntu4.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.3-0ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.3-0ubuntu4)

That update will cause troubles. A dependency wait.
First of all, it does not depend on the current libgjs0b, but instead, libgjs0c.

A new gjs package has been built, but it is not in repos yet.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gjs/1.29.16-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/gjs/1.29.16-0ubuntu2)

Note, that you can install that one only with the gnome-shell_3.1.3-0ubuntu4,
which is in a dependency wait now.

Anyway, more problems:
The latest gnome3 theme just got updated too (gnome-themes-standard_3.1.5-0ubuntu1).
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-themes-standard/3.1.5-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-themes-standard/3.1.5-0ubuntu1)

That, for a surprise, will break the whole theming system with the current gnome-shell_3.1.3-0ubuntu3, leaving you without any theme.

So do not update the gnome-theme-standard, if you are using gnome-shell with the default theming.
Do not update gnome-shell nor gjs either, until this is clear.

Harry, upgrading to the new gnome-themes-standard works just fine here. What exactly doesn't work?

Yes, gjs needed a new library name because the upstream developers keep changing the ABI...and apps that depend on that library would stop working otherwise (fortunately in this case it looks like only gnome-shell uses that library but if it's a system library it has to play by the rules.) Any package that creates a new binary goes into the NEW queue so the archive administrators can look at it first before allowing it in the repository. That will happen soon and the updated gnome-shell will build.

As far as getting gnome-shell 3.1.4 or newer in, we're waiting on an updated clutter build to land in Oneiric. Since I use gnome shell too, I'm interested in getting the newer gnome-shell too but we just have to wait a bit longer. The new gjs was required for gnome-shell 3.1.4 so I'm pretty sure that clutter is the only thing we're still waiting for.

---

### Post by dext on 2011-08-17
> **sgage said:**
> Not for me - all I get is a desktop, no panel or activities.

Any idea when GS 3.1.5 will hit the official repos?

GS-3.1.5 hasnt even been built yet nore is it in the ftp site of gnome [ftp://ftp.gnome.org/pub/GNOME/sources/gnome-shell/3.1/](ftp://ftp.gnome.org/pub/GNOME/sources/gnome-shell/3.1/)

---

### Post by sgage on 2011-08-17
> **dext said:**
> GS-3.1.5 hasnt even been built yet nore is it in the ftp site of gnome [ftp://ftp.gnome.org/pub/GNOME/sources/gnome-shell/3.1/](ftp://ftp.gnome.org/pub/GNOME/sources/gnome-shell/3.1/)

I will possess myself in patience.  :KS

---

### Post by Harry33 on 2011-08-18
> **jbicha said:**
> Harry, upgrading to the new gnome-themes-standard works just fine here. What exactly doesn't work?

Yes, gjs needed a new library name because the upstream developers keep changing the ABI...and apps that depend on that library would stop working otherwise (fortunately in this case it looks like only gnome-shell uses that library but if it's a system library it has to play by the rules.) Any package that creates a new binary goes into the NEW queue so the archive administrators can look at it first before allowing it in the repository. That will happen soon and the updated gnome-shell will build.

As far as getting gnome-shell 3.1.4 or newer in, we're waiting on an updated clutter build to land in Oneiric. Since I use gnome shell too, I'm interested in getting the newer gnome-shell too but we just have to wait a bit longer. The new gjs was required for gnome-shell 3.1.4 so I'm pretty sure that clutter is the only thing we're still waiting for.

**Gnome-themes-standard**
I have one setup (64-bit) where the version 3.1.5 works.
But I use the Staging PPA there with all the packages there are. So I have also the latest gnome-shell git version 3.1.4+git20110816 and Clutter git version 1.7.11~git20110816.
I also have a newer xorg-server (1.10.3.902+git20110815) from Xorg-edgers.

However, my two other setups with gnome-shell 3.1.3 from Oneiric repos (no addidtional PPA's in use) do not work with 3.1.5 gnome-themes-standard. It will destroy the whole theming system leaving the gnome-shell (and also gnome-panel) desktop with no theme at all.
This happens with both my other setups: one is 32-bit (Intel Graphics) and the other 64-bit (ATI Graphics), both with open source drivers.
Then, downgrading to the previous gnome-theme-standard 3.1.2, the issue is gone and I have Adwaita back.

**Gnome-shell**
The gnome shell 3.1.4+git20110816 (from Staging PPA) still depends on libgjs0b, so new gjs naming is not required. In Staging PPA there is the git version 1.29.17~git20110813.

---

### Post by Harry33 on 2011-08-18
The problems with gnome-themes-standard_3.1.5-0ubuntu2 has been reported:

Here (bug #828543)
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/828543](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/828543)

---

### Post by ricotz on 2011-08-18
> **Harry33 said:**
> **Gnome-shell**
The gnome shell 3.1.4+git20110816 (from Staging PPA) still depends on libgjs0b, so new gjs naming is not required. In Staging PPA there is the git version 1.29.17~git20110813.


Renaming the gjs package is needed and standard procedure after API/ABI breaks. 
I dont like to follow these packaging changes before they are really made to avoid diverts. (Of course this could lead to upgrade problems using the ppa packages)

---

### Post by Harry33 on 2011-08-18
> **ricotz said:**
> Renaming the gjs package is needed and standard procedure after API/ABI breaks. 
I dont like to follow these packaging changes before they are really made to avoid diverts. (Of course this could lead to upgrade problems using the ppa packages)

Right, OK.
I can see the ABI bump, switch from libgjs0b to libgjs0c, in your PPA now.

---

