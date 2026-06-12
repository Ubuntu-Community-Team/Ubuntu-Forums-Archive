---
title: "Unmet Dependencies"
date: 2016-01-20
forum: New to Ubuntu
---

### Post by Spencer_Thompson on 2016-01-20
Hello! I'm trying to install xdotool by running the command "sudo apt-get install xdotool git qt-sdk build-essential" and I ran into an error of unmet dependencies. I tried installing the dependencies manually but it says it's already the newest version. I run Ubuntu 14.04 and here's what comes up.

```
~$ sudo apt-get install xdotool git qt-sdk build-essential
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by ajgreeny on 2016-01-21
That does not make any sense as the libcheese packages that are required by unity-control-center, ie greater than 3.4.0 and 3.0.1, are both satisfied by the versions in the normal trusty repos which have 3.10.2-0ubuntu2 of both.

Do you have any held packages that might be stopping the installation of those repo versions?
 Do you have any broken packages showing which you could fix with ```
sudo apt-get install -s -f
```
This will again simulate the fix before carrying it out which you do by removing the -s from the command.
Have you enabled any PPAs that might be having some effect?
Do you have cheese installed, and if so, what version, and do you use it?  If it is not used you might try uninstalling cheese, not those libs, to see if that solves your issue.

---

### Post by ian-weisser on 2016-01-21
> **Spencer_Thompson said:**
> Hello! I'm trying to install xdotool by running the command "sudo apt-get install xdotool git qt-sdk build-essential"

SInce xdotool doesn't seem to need those other packages, why install them?
Are you following instructions from someplace? If so, a link would help.

---

### Post by Spencer_Thompson on 2016-01-21
I used the command "sudo apt-get install -s -f" and it said I had two held back packages, libgbmi and libosmesa6:1386. I also uninstalled Cheese and tried manually installing the dependencies and using the original command but nothing has changed. As to answer ian-weisser, yes I'm trying to set up the program from this site: [https://github.com/katamari1992/ttr-multi-toon](https://github.com/katamari1992/ttr-multi-toon)

```
~$ sudo apt-get install -s -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgbm1 libosmesa6:i386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

