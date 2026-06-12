---
title: "working skype/unmet dependencies"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by robnadeau13 on 2013-03-04
So constantly when I'm trying to install something, I see the output telling me to do "sudo apt-get -f install" to fix some stuff and it never works.. Here's the output:

**robert@roberts-machine:~$ sudo apt-get autoclean**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**robert@roberts-machine:~$ sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  skype:i386
The following packages will be upgraded:
  skype:i386
1 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
1 not fully installed or removed.
Need to get 15.4 kB of archives.
After this operation, 36.7 MB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner skype i386 4.1.0.20.0-0ubuntu0.12.04.2 [15.4 kB]
Fetched 15.4 kB in 3s (4,149 B/s)
dpkg: dependency problems prevent configuration of skype:i386:
 skype-bin:i386 (4.1.0.20.0-0ubuntu0.12.04.2) breaks skype (<< 4.1.0.20.0-0ubuntu0.12.04.1) and is installed.
  Version of skype:i386 to be configured is 4.1.0.20-1.
dpkg: error processing skype:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


The thing is Skype works perfectly so if by fixing that, I'll mess it up - maybe I'll leave it. I just don't know why it's messed up like that...

Any input?

---

### Post by Bashing-om on 2013-03-04
robnadeau13; Hi ! Welcome back.

Not sure of the source of that problem. However try this and see what results;
Terminal code:
```
sudo dpkg --configure skype:i386
```
Failing that might try to (un)install skype:i386 and (re)install it .
[INDENT=2]
just my opinion

[/INDENT]

---

### Post by robnadeau13 on 2013-03-08
Hi thanks for your response! That didn't work but at least you had an idea for me. I guess I'm going to have to uninstall it and reinstall it. I'll try that tomorrow. I wonder exactly what's happening. I've only been using linux for like 2 or 3 weeks.. So I'm very inexperienced however - looking at this line:

[COLOR=#000000]skype-bin:i386 (4.1.0.20.0-0ubuntu0.12.04.2) breaks skype (<< 4.1.0.20.0-0ubuntu0.12.04.1) and is installed.
[/COLOR][COLOR=#000000]Version of skype:i386 to be configured is 4.1.0.20-1.[/COLOR][COLOR=#000000]
[/COLOR]
It looks like, and I may be wrong it's trying to configure an older version of skype than the version I have installed? So I wonder if I could tell it to ignore that version or get rid of the files from that version?
I bet uninstalling and reinstalling will be the only way.. Thanks for your help!!


robert@roberts-machine:~$ sudo dpkg --configure skype:i386
[sudo] password for robert: 
dpkg: dependency problems prevent configuration of skype:i386:
skype-bin:i386 (4.1.0.20.0-0ubuntu0.12.04.2) breaks skype (<< 4.1.0.20.0-0ubuntu0.12.04.1) and is installed.
Version of skype:i386 to be configured is 4.1.0.20-1.
dpkg: error processing skype:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype:i386
robert@roberts-machine:~$

---

### Post by Bashing-om on 2013-03-08
robnadeau13;
Sorry to have left you high and dry, Things came up I had to attend to, came back to my system all messed up, still putting it back together. (grand children ???) No biggy just an aggravation.
Back to your situation. I agree, looks as if you have two instances of skype installed. To see what is on the system at this time do terminal code:
```
sudo apt-cache policy skype:i386
``` see what it returns and go from there. Hopefully we will know which to (un)install,[INDENT=2]
Try'n to help

[/INDENT]

---

### Post by black veils on 2013-03-08
i've seen this sort of thing before, try removing [COLOR=#000000]skype-bin:i386 and any other skype items, then install skype.


[/COLOR]

---

