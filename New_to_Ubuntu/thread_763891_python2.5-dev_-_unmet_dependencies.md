---
title: "python2.5-dev - unmet dependencies"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by DamonChyld on 2008-04-23
I am trying to get hplip-2.8.4 (for my HP printer) installed on my laptop but am running into a snag with python2.5-dev. Google search returns a surprising lack of info, any help would be appreciated.

hplip-2.8.4 installer gives me:
```
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libcupsys2'
Please wait, this may take several minutes...
Running 'sudo apt-get install --yes --force-yes python2.5-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?
```

apt-get gives me:
```
damien@laptop:~/Desktop$ sudo apt-get install --yes --force-yes python2.5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.5-dev: Depends: python2.5 (= 2.5.1-5ubuntu5) but 2.5.1-5ubuntu5.1 is to be installed
E: Broken packages

```

In Synaptic:
I can not reinstall python2.5, only complete remove or remove; if I select remove it wants to take apart my whole system.
Trying to install python2.5-dev gives a unresolvable dependency error.

---

### Post by Oldsoldier2003 on 2008-04-23
> **DamonChyld said:**
> I am trying to get hplip-2.8.4 (for my HP printer) installed on my laptop but am running into a snag with python2.5-dev. Google search returns a surprising lack of info, any help would be appreciated.

hplip-2.8.4 installer gives me:
```
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libcupsys2'
Please wait, this may take several minutes...
Running 'sudo apt-get install --yes --force-yes python2.5-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?
```

apt-get gives me:
```
damien@laptop:~/Desktop$ sudo apt-get install --yes --force-yes python2.5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.5-dev: Depends: python2.5 (= 2.5.1-5ubuntu5) but 2.5.1-5ubuntu5.1 is to be installed
E: Broken packages

```

In Synaptic:
I can not reinstall python2.5, only complete remove or remove; if I select remove it wants to take apart my whole system.
Trying to install python2.5-dev gives a unresolvable dependency error.

what version of Ubuntu are you running on the laptop?

---

### Post by DamonChyld on 2008-04-23
Gibbon (7.10)

edit: why did they take that info off with the reorganization of the forums? It used to show what version you were running under your name on all your posts.

---

### Post by Oldsoldier2003 on 2008-04-23
> **DamonChyld said:**
> Gibbon (7.10)

edit: why did they take that info off with the reorganization of the forums? It used to show what version you were running under your name on all your posts.

I am not sure because I switched to hardy early on, but I don't think python 2.5 is in the gutsy repos.

---

### Post by DamonChyld on 2008-04-23
Python2.5 shows as installed in synaptic but I am not able to reinstall it (greyed out), only remove or complete remove.

---

### Post by Perfect Storm on 2008-04-23
Have you manually installed any packages or used an un-official source in your source list?

---

### Post by DamonChyld on 2008-04-23
I manually installed both VB and Wine, and they are the only two non-ubuntu deb's I have in sources.list. 

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/ 
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

The only other thing that I manually installed was GCStar, a collection management database.

---

### Post by Perfect Storm on 2008-04-23
Okay, thry this;

```
sudo apt-get update && sudo apt-get upgrade
```

It might solve your problem. It could be that your sourcelist needed to be updated and packages upgraded.

Or try use aptitude instead and see if it can solve your dependency problem.

---

### Post by DamonChyld on 2008-04-23
Ok, it looks like aptitude will solve the dependency problem. It gives the following output:
```
:~/ies4linux-2.99.0.1$ sudo aptitude install python2.5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  python2.5-dev 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1877kB of archives. After unpacking 5566kB will be used.
The following packages have unmet dependencies:
  python2.5-dev: Depends: python2.5 (= 2.5.1-5ubuntu5) but 2.5.1-5ubuntu5.1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
python2.5 [2.5.1-5ubuntu5.1 (now) -> 2.5.1-5ubuntu5 (gutsy)]
python2.5-minimal [2.5.1-5ubuntu5.1 (now) -> 2.5.1-5ubuntu5 (gutsy)]

Score is 114

Accept this solution? [Y/n/q/?] 

```

I am afraid to follow it's advise to downgrade though as so much of Gibbon relies on python2.5. Should I say yes to accept or is it dangerous?

---

### Post by Perfect Storm on 2008-04-23
Somehow you have an unofficial python package installed (properly from an unofficial source in the repo - you installed something that required another version of Python).

But before you say Yes, check [http://packages.ubuntu.com/](http://packages.ubuntu.com/) here and see what and which version of python that is official. More over you can download both python and -dev from there instead if you're in doubt if something in the sourcelist is conflicting.

---

### Post by DamonChyld on 2008-04-23
[http://packages.ubuntu.com/gutsy/python2.5](http://packages.ubuntu.com/gutsy/python2.5) is showing 2.5.1-5ubuntu5.1 and [http://packages.ubuntu.com/gutsy/python2.5-minimal](http://packages.ubuntu.com/gutsy/python2.5-minimal) is showing 2.5.1-5ubuntu5.1 as the correct versions but aptitude it trying to downgrade them?

```
Downgrade the following packages:
python2.5 [2.5.1-5ubuntu5.1 (now) -> 2.5.1-5ubuntu5 (gutsy)]
python2.5-minimal [2.5.1-5ubuntu5.1 (now) -> 2.5.1-5ubuntu5 (gutsy)]
```

---

### Post by Perfect Storm on 2008-04-23
But they are exactly the same in number and name....I guess it's safe to do so.

Don't shoot me if it aren't :KS

---

### Post by DamonChyld on 2008-04-23
It's trying to downgrade them to 2.5.1-5ubuntu5 from 2.5.1-5ubuntu5.1. Any way for a non-programing type to ID what moving down to 5 from 5.1 might do? I would hate to have to reinstall! I never could get QuickStart or tar backups to restore so I have to do it all manually :(

---

### Post by Perfect Storm on 2008-04-23
Perhaps wait to get a third opinion(forum member) to give their thought, before doing anything.

---

### Post by DamonChyld on 2008-04-23
Good advice and thank you for all your help A.I. 

Does anyone have any another perspective on this?

---

### Post by forrestcupp on 2008-04-23
Did you try doing what was suggested before and type?
```
sudo apt-get update
sudo apt-get upgrade
```
I suspect that would fix your problem.

---

### Post by DamonChyld on 2008-04-23
Yes, I did update/upgrade but it did not resolve the issue.

```
:~$ sudo apt-get update
[sudo] password for:
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:2 http://archive.ubuntu.com gutsy Release.gpg [191B]                       
Ign http://archive.ubuntu.com gutsy/main Translation-en_US                     
Get:3 http://www.virtualbox.org gutsy Release.gpg [189B]                       
Ign http://www.virtualbox.org gutsy/non-free Translation-en_US                 
Hit http://archive.canonical.com gutsy Release                                 
Ign http://archive.ubuntu.com gutsy/universe Translation-en_US                 
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_US               
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_US               
Hit http://archive.ubuntu.com gutsy Release                                    
Hit http://www.virtualbox.org gutsy Release                                    
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://archive.ubuntu.com gutsy/main Packages                              
Hit http://www.virtualbox.org gutsy/non-free Packages                          
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://archive.ubuntu.com gutsy/universe Packages                          
Hit http://archive.ubuntu.com gutsy/restricted Packages                        
Hit http://archive.ubuntu.com gutsy/multiverse Packages                        
Hit http://archive.ubuntu.com gutsy/universe Sources                           
Hit http://archive.ubuntu.com gutsy/main Sources                               
Hit http://archive.ubuntu.com gutsy/multiverse Sources                         
Hit http://archive.ubuntu.com gutsy/restricted Sources                         
Ign http://wine.sourceforge.net binary/ Release.gpg                           
Ign http://wine.sourceforge.net binary/ Translation-en_US                     
Hit http://wine.sourceforge.net binary/ Release                               
Ign http://wine.sourceforge.net binary/ Packages
Hit http://wine.sourceforge.net binary/ Packages
Get:4 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US
Hit http://packages.medibuntu.org gutsy Release
Ign http://packages.medibuntu.org gutsy/free Packages                          
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Ign http://packages.medibuntu.org gutsy/free Sources                           
Ign http://packages.medibuntu.org gutsy/non-free Sources                       
Hit http://packages.medibuntu.org gutsy/free Packages                          
Hit http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://packages.medibuntu.org gutsy/free Sources                           
Hit http://packages.medibuntu.org gutsy/non-free Sources                       
Fetched 4B in 60s (0B/s)                                                       
Reading package lists... Done
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:~$ sudo apt-get install python2.5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.5-dev: Depends: python2.5 (= 2.5.1-5ubuntu5) but 2.5.1-5ubuntu5.1 is to be installed
E: Broken packages

```

---

### Post by Perfect Storm on 2008-04-23
hmmm...try disable all un-official sources in your source-list and try again.

Also how's your sourcelist looks like?

---

### Post by DamonChyld on 2008-04-23
Ok, looks like we got it working. My sources.list had multiverse repositories commented out (though I had them selected in synaptic). I manually uncommented those and python passed the installer. Thanks a lot for all your help A.I.

sources.list
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
#deb http://www.virtualbox.org/debian gutsy non-free
#deb http://wine.sourceforge.net/apt/ binary/
```

---

