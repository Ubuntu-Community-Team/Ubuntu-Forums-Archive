---
title: "NooB To Ubuntu killed &quot;add/remove&quot;"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by itsguardianjon on 2008-08-30
i dont know what i did other that adding in software thru add/remove and now it doesnt work its displays

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

i tried what is says to do but still nothing 

Heres the source list

guardian@Linux:~$ cat /etc/apt/sources.list#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by neurostu on 2008-08-30
> reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

did you open a terminal and run:
```

sudo apt-get update 
or
sudo apt-get install -f

```
?

---

### Post by Vivaldi Gloria on 2008-08-30
Also try synaptic rather than add-remove. It's in the top panel, system menu > admin.

---

### Post by terry_gardener on 2008-08-30
found this solution from another post, it should help with this problem. 

Open the Synaptic package manager. System --> Administration --> Synaptic Package Manager

If anything is broken it will tell you.
Choose 'Custom' from the buttons at the bottom then click on 'Broken'

Right click on the offending package and choose to remove it.

i taken this solution from [http://ubuntuforums.org/showthread.php?t=129158](http://ubuntuforums.org/showthread.php?t=129158) post #3

---

### Post by itsguardianjon on 2008-08-30
i tried the synaptic package manager and i get this message



E: Type '--11:39:54--' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



should i just reintall ubuntu???

---

### Post by arpanaut on 2008-08-30
> **itsguardianjon said:**
> i tried the synaptic package manager and i get this message



E: Type '--11:39:54--' is not known on line 1 in source list **/etc/apt/sources.list.d/mediauntu.list**
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



should i just reintall ubuntu???

Did you try to add the medibuntu repository to your sources ?
If so you did something wrong... see bold above... I'm not sure how to fix it.

Try reversing what you did, and then follow the instructions on this link: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Last error may be from having more than one package manager open at the same time.

Usually things can be solved without to reinatall, but if you haven't gone to far with your install and havent much to lose ... your call?

When I was new to Ubuntu I must have reinstalled a dozen times or so in the first month or two whenever I screwed things up.(LOL) But I finally learned what NOT to do, amd how to recover from apparently impossible situations, it just takes some time and research to get your bearings

Good Luck!

---

### Post by knattlhuber on 2008-08-30
> **itsguardianjon said:**
> i tried the synaptic package manager and i get this message



E: Type '--11:39:54--' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



should i just reintall ubuntu???

No, don't reinstall. This looks like a typo in '/etc/apt/sources.list.d/medianuntu.list'.

Please post the output of

```
cat /etc/apt/sources.list.d/medianuntu.list
```

Also, 'medianuntu' doesn't sound right.. should be 'medibuntu' ?!

---

### Post by itsguardianjon on 2008-08-31
guardian@Linux:~$ cat /etc/apt/sources.list.d/medibuntu.list
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
guardian@Linux:~$

---

### Post by knattlhuber on 2008-08-31
> **itsguardianjon said:**
> guardian@Linux:~$ cat /etc/apt/sources.list.d/medibuntu.list
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
guardian@Linux:~$

Well, that file looks OK.

I think the key to your problem is this line

```
E: Type '--11:39:54--' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list
```

There seems to be a rogue file in the folder and that confuses apt-get. 

Could you please post the output of

```
ls /etc/apt/sources.list.d -l
```

---

### Post by itsguardianjon on 2008-09-01
guardian@Linux:~$ '--11:39:54--' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list
bash: --11:39:54--: command not found
guardian@Linux:~$ ls /etc/apt/sources.list.d -l
total 8
-rw-r--r-- 1 root root 156 2008-08-30 11:39 mediauntu.list
-rw-r--r-- 1 root root 226 2008-03-28 04:58 medibuntu.list
guardian@Linux:~$

---

### Post by Gregmond on 2008-09-01
> **itsguardianjon said:**
> guardian@Linux:~$ cat /etc/apt/sources.list.d/medibuntu.list


It looks like knattlhuber is right.

try:
```
cat /etc/apt/sources.list.d/mediauntu.list
```

I believe that you need to remove that file but I am not an expert on .list files or how these are used.

---

### Post by knattlhuber on 2008-09-01
> **itsguardianjon said:**
> guardian@Linux:~$ '--11:39:54--' is not known on line 1 in source list /etc/apt/sources.list.d/mediauntu.list
bash: --11:39:54--: command not found
guardian@Linux:~$ ls /etc/apt/sources.list.d -l
total 8
-rw-r--r-- 1 root root 156 2008-08-30 11:39 mediauntu.list
-rw-r--r-- 1 root root 226 2008-03-28 04:58 medibuntu.list
guardian@Linux:~$

There we have the culprit: 'mediauntu.list'. Probably a typo while adding repos to sources.list. You can simply remove the file by doing

```
sudo rm /etc/apt/sources.list.d/mediauntu.list
```

Afterwards, run

```
sudo apt-get update
```

and see what happens.

---

### Post by itsguardianjon on 2008-09-02
Yeah I reinstalled ubuntu. but thanx for all the help from all of you knowing me ill need it again soon.  so i guess this thread is now closed.

---

### Post by gabe.c on 2008-09-17
i have a similar problem. the output i got from ls /etc/apt/sources.list.d -l 
is this:
total 4
-rw-r--r-- 1 root root 471 2008-09-17 20:46 winehq.list
is there something else i could do?

---

