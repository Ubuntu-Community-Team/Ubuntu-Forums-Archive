---
title: "broken packages wont fix"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by biglove on 2013-02-26
Ive been anting to watch video files on my desktop but the player needs some plug ins so i go to install them but it tells me that i got 4 broken packages om y computer. i try fixing with synaptic package manager as recommended by several people on this site but with no success but i get this 
[I]
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies[/I]

i have tried the following commands in terminal

[I]sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove[/I]

but with no success however when i punched in *sudo apt-get install -f *i got told that it failed to correct the following dependences

[I] libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.12) but 2.15-0ubuntu10.3 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies[/I]

any help on this would be appreciated.

---

### Post by Kopkins on 2013-02-26
Show output of sudo apt-get install.

Try sudo apt-get dist-upgrade -f

Kopkins

---

### Post by matt_symes on 2013-02-26
Hi

I would like to check your software sources.

Open a terminal and type

```
grep -v "^#" /etc/apt/sources.list /etc/apt/sources.list.d/*
```Copy and paste the output of that command into your next post.

Wrap the output of the command between code tags like this 

[noparse]```
text
```[/noparse] 

to get output like this ```
text
```Kind regards

---

### Post by biglove on 2013-02-27
[sudo apt-get dist-upgrade -f]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.12) but 2.15-0ubuntu10.3 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
[/sudo apt-get dist-upgrade -f]

[grep -v "^#" /etc/apt/sources.list /ect/apt/sources.list.d/*]
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
grep: /ect/apt/sources.list.d/*: No such file or directory
[/grep -v "^#" /etc/apt/sources.list /ect/apt/sources.list.d/*]

[sudo apt-get install]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.12) but 2.15-0ubuntu10.3 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Unmet dependencies. Try using -f.
[/sudo apt-get install]

---

### Post by matt_symes on 2013-02-27
Hi

There was a typo in my last command.

can you post the output of

```
grep -v "^#" /etc/apt/sources.list.d/*
```

This will show me the rest of your sources.

dependency issues are often caused by mismatched sources.

Kind regards

---

### Post by biglove on 2013-02-27
hi
here you go

[grep -v "^#" /etc/apt/sources.list.d/*]
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.distUpgrade:deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.save:deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
[/grep -v "^#" /etc/apt/sources.list.d/*]

i don't think I'm doing it right with the ```
text
``` thing

thanks

---

### Post by matt_symes on 2013-02-27
Hi

This is one of your sources from your sources.list file.

```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
```It is for precise.

This is the source from your ppa file

```
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
```It is for Lucid.

Lucid came out on April 2010. Precise came out in April 2012.

The actual ppa files themsleves are not referenced anymore as they do not have a .list extension

```
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.distUpgrade
/etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.save
```Precises libraries are much newer than lucids and this is why you are having the library mismatch and dependencies problem.

You have a mismatch of libraries from precise and lucid.

libc-bin-2.11.1-0ubuntu7.12 is from lucid and libc6 depends on it.
libc-bin-2.15-0ubuntu10.3 is actually installed and is from precise.

Therefore libc6 is a library from lucid

> 
[I]libc6: Depends: libc-bin (= 2.11.1-0ubuntu7.12) but 2.15-0ubuntu10.3 is installed
         Recommends: libc6-i686
  python-louis: Depends: liblouis0 (>= 1.7.0-2) but it is not installable
  ubuntu-minimal: Depends: libc6-i686
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies[/I]Unfortunately libc6 is a pretty fundamental library so we have to tread very carefully.

BTW: This is an upgrade from Lucid->Precise ?

I believe libc6 was pulled in from that wine lucid ppa or from a hangover from an upgrade from lucid to precise.

Anyhow, it's a problem.

So let's try to fix your problem.

I am going to assume you have wine installed here. If not do not follow these steps and post back.

From here, there is a precise version of the ppa and this is the version you should be using not lucids.

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/)

Open a terminal and copy and paste this into it. Copy and paste is less error prone.

```
sudo cp /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list.save /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
``````
sudo sed -i 's/lucid/precise/g' /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
``````
sudo apt-get update
``````
sudo apt-get install -f
```Post back on efficacy.

Kind regards

---

### Post by audiomick on 2013-02-27
> **biglove said:**
> 

i don't think I'm doing it right with the ```
text
``` thing

thanks

Look for the button at the top of the post window that is marked with #

When you press that, it will generate code tags that look like this

[noparse] ```

``` [/noparse]

You can also type them in by hand.

You need to have the first one [noparse] ```
 [/noparse] before the stuff you want in the code box, and the second one [noparse]
``` [/noparse] after it.

You can generate the tags and then type or paste your text between them, or type or paste your text into the post window, run the mouse over it to select it, then click on the code tags button, the # .

---

