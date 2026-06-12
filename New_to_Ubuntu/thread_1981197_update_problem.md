---
title: "update problem"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by bgbh on 2012-05-16
When update manager is run I get the following message



E: The package gpar2 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

W: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

---

### Post by Cavsfan on 2012-05-16
> **bgbh said:**
> When update manager is run I get the following message



E: The package gpar2 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

W: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

A very knowledgeable friend in this forum **ranch hand** calls Update Manager Update Mangler.
He told me to always use these commands to get my updates:

```
sudo apt-get update 
sudo apt-get upgrade
```If there is anything held back like a new kernel install this will get that:
```
sudo apt-get dist-upgrade
```.

You pretty much cannot go wrong getting updates in this manner.

You can even setup a script to do this by entering **gksu gedit /home/cavsfan/.bashrc** (replacing cavsfan with your login name)

Then toward the bottom of the file enter this:

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
```You'll have to logout and back in for it to take effect.
But, then you will just enter "**ud**" and "**ud2**" in terminal.

Although you can name them whatever you want. You're not stuck with ud and ud2.

---

### Post by Cavsfan on 2012-05-16
> **bgbh said:**
> file 'getdeb.list.bck'  

Here is the solution:

[http://ubuntuforums.org/showthread.php?t=1652327](http://ubuntuforums.org/showthread.php?t=1652327)

It sounds like you have some sources mixed up like you did a recent upgrade.
That link should fix the problem. I still recommend the update method I mentioned.

---

### Post by bgbh on 2012-05-17
Still the same
even tried sudo dpkg --remove --force-remove-reinstreq gpar2 and got the following
sudo] password for brett: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 154917 files and directories currently installed.)
Removing gpar2 ...
/var/lib/dpkg/info/gpar2.postrm: 33: update-desktop-database: not found
dpkg: error processing gpar2 (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 gpar2

---

### Post by philinux on 2012-05-17
Ranch Hand's term for UM is appropriate during the development cycle. For a stable release it's spot on and does it's job correctly.

---

### Post by philinux on 2012-05-17
> **bgbh said:**
> Still the same
even tried sudo dpkg --remove --force-remove-reinstreq gpar2 and got the following
sudo] password for brett: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 154917 files and directories currently installed.)
Removing gpar2 ...
/var/lib/dpkg/info/gpar2.postrm: 33: update-desktop-database: not found
dpkg: error processing gpar2 (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 gpar2

Post the output of these.

```
ls /etc/apt/sources.list.d

cat /etc/apt/sources.list
```

---

### Post by bgbh on 2012-05-17
brett@brett-Mint12KDE ~ $ ls /etc/apt/sources.list.d
alza-project-oneiric.list            getdeb.list                   kubuntu-ppa-ppa-oneiric.list.save
alza-project-oneiric.list.save       getdeb.list.bck               local-repository.list
blca-published-oneiric.list          getdeb.list.save              local-repository.list.save
blca-published-oneiric.list.save     jcfp-ppa-oneiric.list         tualatrix-ppa-oneiric.list
clipgrab-team-ppa-oneiric.list       jcfp-ppa-oneiric.list.save    tualatrix-ppa-oneiric.list.save
clipgrab-team-ppa-oneiric.list.save  kubuntu-ppa-ppa-oneiric.list
brett@brett-Mint12KDE ~ $ cat /etc/apt/sources.list
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) lisa main upstream import
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) lisa-kde main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
deb [http://ppa.launchpad.net/msb/ppa/ubuntu](http://ppa.launchpad.net/msb/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/msb/ppa/ubuntu](http://ppa.launchpad.net/msb/ppa/ubuntu) oneiric main
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) oneiric main
brett@brett-Mint12KDE ~ $

---

### Post by Cavsfan on 2012-05-17
> **bgbh said:**
> brett@brett-Mint12KDE ~ $ ls /etc/apt/sources.list.d
```
alza-project-oneiric.list            
getdeb.list                   
kubuntu-ppa-ppa-oneiric.list.save
alza-project-oneiric.list.save       
getdeb.list.bck               
local-repository.list
blca-published-oneiric.list          
getdeb.list.save              
local-repository.list.save
blca-published-oneiric.list.save     
jcfp-ppa-oneiric.list         
tualatrix-ppa-oneiric.list
clipgrab-team-ppa-oneiric.list       
jcfp-ppa-oneiric.list.save    
tualatrix-ppa-oneiric.list.save
clipgrab-team-ppa-oneiric.list.save  
kubuntu-ppa-ppa-oneiric.list
```brett@brett-Mint12KDE ~ $ cat /etc/apt/sources.list
```
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) lisa main upstream import
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) lisa-kde main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb apps
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) oneiric-getdeb games
deb [http://ppa.launchpad.net/msb/ppa/ubuntu](http://ppa.launchpad.net/msb/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/msb/ppa/ubuntu](http://ppa.launchpad.net/msb/ppa/ubuntu) oneiric main
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) oneiric main
```brett@brett-Mint12KDE ~ $

I wrapped CODE around your text. You highlight the text and then click the # button at the top right.
Do you know what getdeb.list.bck is used for?

Hopefully philinux can tell you what is wrong because I don't see anything.

---

### Post by philinux on 2012-05-17
Looks like this has cropped up before. Google foo good today.

[http://www.linuxquestions.org/questions/ubuntu-63/cant-remove-deb-in-kubuntu-546217/](http://www.linuxquestions.org/questions/ubuntu-63/cant-remove-deb-in-kubuntu-546217/)

See last post.

And cavsfan is correct nothing suspicious in the lists .

---

