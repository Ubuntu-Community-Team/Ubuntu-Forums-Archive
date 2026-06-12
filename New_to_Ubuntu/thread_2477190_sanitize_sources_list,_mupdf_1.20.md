---
title: "sanitize sources list, mupdf 1.20"
date: 2022-07-17
forum: New to Ubuntu
---

### Post by jindam-vani on 2022-07-17
over period of time, very long list in sources.list. there are very few packages installed, required, used by me. i want to remove as many as possible from file. i just want to install latest stable versions and focal, focal-updates and focal-backports satisfy my needs. should i delete all others? my only concern, why mupdf is   not uptodate?  

sources.list:
```
jindam@localhost:~$ cat /etc/apt/sources.list 
# See http://help.ubuntu.com/community/UpgradeNotes for how to up grade to 
# newer versions of the distribution. 
deb http://ports.ubuntu.com/ubuntu-ports/ focal main restricted 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal main restri cted  
## Major bug fix updates produced after the final release of the ## distribution. 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-updates main rest ricted 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-updates mai n restricted  
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT rec eive any 
## review or updates from the Ubuntu security team. 
deb http://ports.ubuntu.com/ubuntu-ports/ focal universe 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal universe 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-updates universe 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-updates uni verse  
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy your self as to 
## your rights to use the software. Also, please note that softwa re in 
## multiverse WILL NOT receive any review or updates from the Ubu ntu 
## security team. deb http://ports.ubuntu.com/ubuntu-ports/ focal multiverse 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal multiverse 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-updates multivers e 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-updates mul tiverse  
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it  includes 
## newer versions of some applications which may provide useful f eatures. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-backports main re stricted universe multiverse 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-backports m ain restricted universe multiverse  
## Uncomment the following two lines to add software from Canonic al's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonic al and the 
## respective vendors as a service to Ubuntu users. 
# deb http://archive.canonical.com/ubuntu focal partner 
# deb-src http://archive.canonical.com/ubuntu focal partner  
deb http://ports.ubuntu.com/ubuntu-ports/ focal-security main res tricted 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-security ma in restricted 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-security universe 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-security un iverse 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-security multiver se 
# deb-src http://ports.ubuntu.com/ubuntu-ports/ focal-security mu ltiverse
```

regards,
jindam, vani

---

### Post by grahammechanical on 2022-07-17
Please edit your post and replace the word <code> between the square brackets with the word <quote>

It is very difficult to read your sources.list file because it appears as one straight line.

Please give us some information about your hardware. You are using a port of Ubuntu and it might be helpful to know the architecture of the processor. Whether it is ARM or something else. Please run this command and post the results between quote tags.

```
sudo apt update
```

The output may include error messages that explain why you cannot update the system. As regards your sources.list it seems normal to me. It is not easy to study the list because you put the list between code tags. But it seems normal.

Lines preceded with two hashes (##) are comment lines giving information and are not acted on. Lines preceded with a single hash (#) are lines that are commented out and are also not acted on. It is normal to have these lines in our sources.list file.

Regards

P.S. Thank you deadflower

---

### Post by deadflowr on 2022-07-17
Using grep ^deb I cut down your sources.list to the actual sources in use  here:
```
deb http://ports.ubuntu.com/ubuntu-ports/ focal main restricted 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-updates main rest ricted 
deb http://ports.ubuntu.com/ubuntu-ports/ focal universe 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-updates universe 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-updates multivers e 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-backports main re stricted universe multiverse 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-security main res tricted 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-security universe 
deb http://ports.ubuntu.com/ubuntu-ports/ focal-security multiver se 
```

That said, mupdf has never been updated on Ubuntu 20.04, or any other Ubuntu release after their initial releases.
Ubuntu doesn't roll updates for most packages to the latest upstream stable versions.
If you want a newer version you will have to get it from another source.
The most those packages will normally get are security updates, if any. Or possibly small patch-fixes.
But almost never full upgrades to completely new versions.

(There are, of course a handful of exceptions to this, like Firefox.
But those exceptions are very few and very far between)

---

### Post by Holger_Gehrke on 2022-07-17
Those are - as far as I can tell - standard Ubuntu repositories. Nothing in there looks unusual or 'risky' to me. I'd just leave it as is. You might want to take a look into '/etc/apt/sources.list.d/', most unusual repositories or ppa end up as configuration fragments in that directory.

As far as mupdf is concerned, Ubuntu never updates packages within a release (except for the kernel, the web-browser(s) and specific e-mail programs). You might get bug-fixes (back-ported to the release of the program included at release of the Ubuntu version) but no updates to newer versions. It's done that way to have a stable platform for development. If you target a certain release of Ubuntu then you know what versions of programs and libraries are on the system. So with 20.04 you get mupdf 1.16, with 22.04 you get mupdf 1.19 and with 22.10 you'll probably get mupdf 1.20.

Holger

---

### Post by Impavidus on 2022-07-17
There's one missing that you might want to have, given the other repositories you have enabled:```
deb http://ports.ubuntu.com/ubuntu-ports/ focal multiverse
```That's for the multiverse repo (the packages with some legal limitations) that have never been updated.

That has nothing to do with mupdf, which is in universe (the free packages, not supported by Canonical). As mentioned above, for most software you only get important bugfixes. You could try to find an alternative repository (PPA) or installation method, but if this new version isn't extremely important to you, it's best to keep it at the version you get with your release of Ubuntu.

The other repos in your sources.list have already been commented out. Those are the source code repos (deb-src). Most people don't need them, but for legal reasons the source code must be available, so says the GNU General Public License. Also the partner repo has been commented out, but there's nothing interesting in there any more. It used to contain the flash player. You could have additional repositories in other .list files in /etc/apt/sources.list.d/.

---

### Post by deadflowr on 2022-07-17
> There's one missing that you might want to have, given the other repositories you have enabled:
```
deb http://ports.ubuntu.com/ubuntu-ports/ focal multiverse
```
it is enabled, I just missed it doing the code tag clean up.

This line
```
## security team. deb http://ports.ubuntu.com/ubuntu-ports/ focal multiverse 
```
should actually end at team. And a new line should show for deb etc etc.
I missed that.
The original output was a complete mess, so I did the best I could.

---

