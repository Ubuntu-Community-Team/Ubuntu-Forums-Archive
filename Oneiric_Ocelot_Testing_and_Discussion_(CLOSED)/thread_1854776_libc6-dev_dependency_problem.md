---
title: "libc6-dev dependency problem"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bsanyi on 2011-10-05
I've just installed the new ubuntu oneiric server (32 bit version) and I've
found that libc6-dev cannot be installed because of dependency problems.

```

# apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.13-16ubuntu4) but 2.13-20ubuntu4 is to be installed
             Recommends: gcc but it is not going to be installed or
                         c-compiler
E: Unable to correct problems, you have held broken packages.

```I think libc6-dev is really a basic package, so it has to be available
very soon in a new version.

---

### Post by dino99 on 2011-10-05
are you using the "main" server ? (synaptic setting tabs)

latest libc6 is 2.13-20ubuntu5 in oneiric archive

you might need to update

---

### Post by Larkspur on 2011-10-06
If you're still having this problem, bsanyi, check /var/cache/apt/archives/partial for an unfinished download of the package.  I had a similar dependency problem a couple of days ago, and it turned out that the download was interrupted, but whenever I tried to fix the broken packages, synaptic could not resume the download.  If there is an unfinished download, change the name of the package and try to fix the dependencies again.  A new copy should be downloaded.

---

