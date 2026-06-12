---
title: "trying to install banshee"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by fignig on 2008-08-21
and i added the banshee to the repositories so i could install thru synaptic but this keeps popping up when i try and mark banshee for installation:

Depends: libpango1.0-0 (>=1.20.5) but 1.20.1-1 is to be installed

---

### Post by Ryadt on 2008-08-21
> **fignig said:**
> and i added the banshee to the repositories so i could install thru synaptic but this keeps popping up when i try and mark banshee for installation:

Depends: libpango1.0-0 (>=1.20.5) but 1.20.1-1 is to be installed

Try ```
sudo aptitude install banshee
```.

Use aptitude instead of apt-get.

hope it works.

---

### Post by Thermo1 on 2008-09-20
Same problem here:

```
~$ sudo aptitude install banshee-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  banshee-1 
The following NEW packages will be automatically installed:
  libavahi1.0-cil libboo2.0-cil libmono-zeroconf1.0-cil libnotify0.4-cil 
  libtaglib2.0-cil podsleuth 
The following NEW packages will be installed:
  libavahi1.0-cil libboo2.0-cil libmono-zeroconf1.0-cil libnotify0.4-cil 
  libtaglib2.0-cil podsleuth 
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2663kB/3322kB of archives. After unpacking 11.8MB will be used.
The following packages have unmet dependencies:
  banshee-1: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
banshee-1 [Not Installed]

Score is -9881

Accept this solution? [Y/n/q/?]
```

---

### Post by mc4100 on 2008-09-20
Did you add the corret repo for your Ubuntu version:
```
deb http://ppa.launchpad.net/banshee-team/ubuntu **hardy** main
```
Edit: 
After having a better look, your problem just seems to be confirm a PPA issue ... I had a look at the hardy Banshee PPA:

**banshee-1**,
> **Depends**: libpango1.0-0 (>=1.20.5)
but Hardy Universe only has:
> libpango1.0-0 (1.20.1-1)

**Update**
If you add the Gutsy PPA, or simply go to Software Sources, then the third-party tab, select the Banshee team PPA, and **edit** the part that says *"hardy"* to *"gutsy"*, you'll still get the same version. It should now install:
> **Depends**: libpango1.0-0 (>=1.18.3)

---

