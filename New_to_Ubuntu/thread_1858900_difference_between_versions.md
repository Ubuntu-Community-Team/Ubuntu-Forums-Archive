---
title: "difference between versions"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by carranty on 2011-10-13
Hi,

I know this is a really basic question, but what changes between different versions of Ubuntu?  The obvious one is the windows manager/desktop environment (I always get mixed up between those two) and the preinstalled programs, but aside from that what changes? I tend to use openbox rather than the standard interface, run update manager daily and have no problem installing my own programs, so what differs from say 11.04 to 11.10?  Is it worth the hassle of a fresh install?

---

### Post by Anuovis on 2011-10-13
I think you should clarify whether you are interested in differences between different desktop environments for Ubuntu (like Unity, Gnome, KDE, etc.) or between different versions of Ubuntu (like 11.04, 11.10).

Newer versions include all sorts of updates, new functions and such. Long term support releases are more stable than regular ones. 

As for the desktop environments, whatever works for you.

---

### Post by Lisiano on 2011-10-13
Different editions have different Desktop Environments, for example Ubuntu has Gnome (Now switching to Unity), Kubuntu has KDE, Xubuntu has XFCE and Lubuntu has LXDE. Ubuntu Server has no DE by default.

Now the different versions (Say 11.04 and 11.10) have different software versions, the newer the version, the newer the software (Thumb rule), usually if you prefer stable software then it's recommended to use LTS (Long Term Support) they have a tad bit outdated software but compensate for that software being throughly tested. For example, the current *buntus have a 2.6.38 kernel, the next Ubuntu will have a 3.0.0 kernel (Which has some nifty updates).
Hope this answers your question.

---

### Post by aeiah on 2011-10-13
if we're talking about the 6-monthly releases, then the difference is mostly the kernel, modules and additional software available in the repository. sometimes software and libraries aren't at the newest version in previous ubuntu versions (even if the version is still supported) because of conflicts.

the newer versions usually resolve existing bugs, and contain new ones.

---

### Post by carranty on 2011-10-13
[QUOTE=Lisiano;11336791
Now the different versions (Say 11.04 and 11.10) have different software versions, the newer the version, the newer the software (Thumb rule), 
[/QUOTE]

I see, so when I run update manager, it isn't installing the newer versions of the software.  What does update manager install then?  Bug fixes for the existing versions and what not......

---

### Post by carranty on 2011-10-13
> **Anuovis said:**
> I think you should clarify whether you are interested in differences between different desktop environments for Ubuntu (like Unity, Gnome, KDE, etc.) or between different versions of Ubuntu (like 11.04, 11.10).


I'm interested in the differences between versions, not differences between desktop environments.

---

### Post by Anuovis on 2011-10-13
In my limited experience, LTS releases were more stable than others. Also, April releases seemed to have less bugs and such compared to October Ubuntus. But that might be different for everyone.

And yes, you do get newer software, kernels, newer interfaces and such. I wouldn't bother chasing every new version unless you need some fancier stuff that comes with it. Doing an install every 6 months just seems bothersome.

Also, you probably noticed that some releases bring more changes than others. Like 11.04 that introduced the whole new desktop environment, Unity. It might be useful to check the changes before installing on Ubuntu page.

---

### Post by carranty on 2011-10-13
Thanks for the responses guys.

---

### Post by BlinkinCat on 2011-10-13
Long term support (LTS) releases come out every two years in April -

ie  8.04  10.04   12.04

They are supported for three years.

---

### Post by kaldor on 2011-10-13
Update manager is giving you security updates and patches. You won't be getting the latest and greatest software- it's just patches for existing versions.

11.04, 11.10, 12.04, etc, are all different releases of Ubuntu. Think Windows XP, Windows Vista, Windows 7. New releases of Ubuntu come out every 6 months, and every 2 years there's a "LTS" release.

---

### Post by alphacrucis2 on 2011-10-13
> **carranty said:**
> I see, so when I run update manager, it isn't installing the newer versions of the software.  What does update manager install then?  Bug fixes for the existing versions and what not......

It installs bug fixes and security fixes. Sometimes new versions are provided as backports. What most people do to get new versions is add ppa's to their software sources. Then update manager will check those ppa's for newer versions. For example the mozilla stable ppa will get you the latest stable version of Firefox. They also have the Mozilla next ppa which rolls through beta's through to release. ppa's are generally not official, so won't be supported by Ubuntu. Any problems and you would have to report to the ppa maintainer, or upstream to the actual developers of the particular software.

FYI. Here is the link to the Mozilla stable ppa on launchpad.

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

