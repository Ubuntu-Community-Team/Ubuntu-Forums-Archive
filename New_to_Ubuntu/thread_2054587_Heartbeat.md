---
title: "Heartbeat"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by edsh on 2012-09-07
Hello I am try to installing Heardbeat on ubuntu 10.04... can any one help me????

---

### Post by GreatDanton on 2012-09-07
If you post how did you try to install it, and any errors you received, then we will be able to help you.

Regards.

---

### Post by Epodx64 on 2012-09-07
I just Googled heardbeat and I can't seem to figure out what exactly it is?

---

### Post by NikTh on 2012-09-08
> **edsh said:**
> Hello I am try to installing Heardbeat on ubuntu 10.04... can any one help me????

Hi , 
heartbeat = [http://packages.ubuntu.com/lucid/heartbeat](http://packages.ubuntu.com/lucid/heartbeat) 

is this the package ? 

You know , It seems strange to me , a user who wants to install such special package but don't know how to install it. 

Are sure is this the package ? 

Maybe you meant Handbrake ? [http://ubuntuforums.org/showthread.php?t=1771099](http://ubuntuforums.org/showthread.php?t=1771099) ... No ? 

____________________________________________________________________

**To install Heartbeat** you must enable Universe Repositories. Check it out from 
```
gksudo software-properties-gtk
``` and at the first section see if 
"Community-maintained free and open-source software (universe)" is ticked. 

Then from terminal you can install it by 
```
sudo apt-get update 
sudo apt-get install heartbeat
```Thanks

---

### Post by nexusguy59 on 2013-04-03
I am no dummy when it comes to this and I can't install it, it's ridiculous I have to go hunt down all these packges.

apt-get install heartbeat does not work.

root@loadb1:~# apt-get install heartbeat
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 heartbeat : Depends: libheartbeat2 (>= 1:3.0.5) but it is not going to be installed
             Depends: libpils2 (>= 1.0.8) but it is not going to be installed
             Depends: libplumb2 (>= 1.0.8) but it is not going to be installed
             Depends: libplumbgpl2 (>= 1.0.8) but it is not going to be installed
             Depends: libstonith1 (>= 1.0.8) but it is not going to be installed
             Depends: cluster-glue but it is not going to be installed
             Depends: gawk
             Depends: libxml2-utils
             Depends: resource-agents but it is not going to be installed
             Recommends: pacemaker (>= 1.0.6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Sorry but i am extremely frustrated after searching for 3 hours to get this installed, yes my universe packages are enabled

---

### Post by alphacrucis2 on 2013-04-03
I was curious about this as we use heartbeat with Linux clusters at work using CentOS. I just tried installing it in Ubuntu 13.04 and all the package dependencies were met and installed ok. The OP referred to Ubuntu 10.04 so maybe there is a problem with the repos or conflicting PPA's.  @nexusguy59 - which version are you using? I presume you are running a server version as there isn't much point to heartbeat on a standalone desktop or laptop?

---

