---
title: "No Hardy updates"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by urvaksh on 2008-05-01
Ever since I installed Hardy last Firday I have not received any updates from the update manager. 
Is this normal. I would get updates in Gutsy almost every two or three days..
Thanks

---

### Post by Myglaren on 2008-05-01
Not normal.
I installed yesterday and recieved updates today.

---

### Post by bapoumba on 2008-05-01
Same here.
Updates on a stable release are security or bug fixes (sometimes backported packages). Just give it some time before these pop in :)

Edit: to make it clear, I did not get updates either, and I have all the ubuntu repos (main, restricted, universe, multiverse). So same as the OP and next poster.

---

### Post by Tatty on 2008-05-01
Myglaren, Did you install the final release of Hardy? Have you enabled any extra repos?

I have not recieved any updates either, i dont think there have been any.  If you want to force a check for updates do: ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by arpanaut on 2008-05-01
updates? UPDATES?
We don't no stinking updates...
HARDY's freaking perfect!

No?

Seriously thou...
See bapoumba's post above. also I think many of the developers are at a retreat right now laying out their diabolical plan for the Insane Ibex... hehe
I expect many updates, fixes , etc. coming in the next couple of weeks.

Have Patience.

---

### Post by timzak on 2008-05-01
The only updates I've gotten so far have been from Medibuntu repositories.

---

### Post by Cap'n Redbeard on 2008-05-01
Hi Folks,

i've had a similar update problem. Installed Hardy over Gutsy four days ago and recieved daily updates until yesterday (30/4/8). Since midnight, i've got this:

> [SIZE="1"]redbeard@Redbeard-desktop:~$ sudo apt-file update
[sudo] password for redbeard: 
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz) (404)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz) (404)
redbeard@Redbeard-desktop:~$ [/SIZE]


Could there be a problem with a server somewhere ? i can't contact any of the above URL's elsewhere (not found error).

Any ideas ?  :confused:

---

### Post by Myglaren on 2008-05-01
> **Tatty said:**
> Myglaren, Did you install the final release of Hardy? Have you enabled any extra repos?

I have not recieved any updates either, i dont think there have been any.  If you want to force a check for updates do: ```
sudo apt-get update && sudo apt-get upgrade
```

I'm assuming so, did an upgrade from Gutsy so I would assume all packages would be up to date.

---

### Post by bapoumba on 2008-05-01
Cap'n Redbeard, I cannot get to the repo that is giving you errors. Please post your sources.list:
```
cat /etc/apt/sources.list
```

Edit: looks like its a gutsy repo.

---

### Post by wermeulen on 2008-05-01
Check the [Security Announce]("https://lists.ubuntu.com/archives/ubuntu-security-announce/") mailinglist archive for Ubuntu--no updates since the 22nd of April.

But I was worried also' I'm missing my daily updates :)

---

### Post by Daveg4otu on 2008-05-01
Updated to HH on 25th.....

Updates.......zilch
Problems .....zilch
Contentment...100%

---

### Post by peakshysteria on 2008-05-01
No updates here either. I was worried. Now I'm not :) [Security announce]("https://lists.ubuntu.com/archives/ubuntu-security-announce/")

---

### Post by urvaksh on 2008-05-01
Thanks ya'll...

---

### Post by Cap'n Redbeard on 2008-05-03
Hi bapoumba,

Repo list:

> redbeard@Redbeard-desktop:/etc/apt$ cat sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main
redbeard@Redbeard-desktop:/etc/apt$ 


Now, having looked at the various URL's that "apt-file update" tries to read the files from, the directories are there but the ".gz" archives are missing.

Yes whilst most of these are Gutsy repo's, the files in these lists should build just the same under Hardy with "apt".

Is this any help ? :)

---

### Post by bapoumba on 2008-05-04
You need to change all the **gutsy** occurrences in your sources.list to **hardy**. You cannot mix repos from two different releases.
lease open a terminal:
```
sudo nano -B /etc/apt/sources.list
```
Make the changes.
Save the file with CTRL-O (same name)
Exit nano with CTRL-X
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Cap'n Redbeard on 2008-05-04
Hi bapoumba,

Thanks, i've followed your suggestion, changing all the "gutsy"'s to "hardy" in the "sources.list" file.

Then did "sudo apt-get update" and "sudo apt-get dist-upgrade".

Apt said this:

> W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy_main_i18n_Translation-en%5fGB)
W: You may want to run apt-get update to correct these problems
redbeard@Redbeard-desktop:~$ sudo apt-get dist-upgrade


so after the last command above i did "sudo apt-get update".

However, sudo apt-file update still can't finde the files it's after.

The problem with this of course is apt doesn't know where to look for any files !

Any ideas ? :confused:

---

### Post by Joeb454 on 2008-05-04
Are you running Ubuntu 7.10? If so then you should actually have the sources.list say Gutsy not Hardy - and then do a dist-upgrade.

If not just ignore me completely :)

---

### Post by bapoumba on 2008-05-04
> **Cap'n Redbeard said:**
> Hi bapoumba,

Thanks, i've followed your suggestion, changing all the "gutsy"'s to "hardy" in the "sources.list" file.

Then did "sudo apt-get update" and "sudo apt-get dist-upgrade".

Apt said this:



so after the last command above i did "sudo apt-get update".

However, sudo apt-file update still can't finde the files it's after.

The problem with this of course is apt doesn't know where to look for any files !

Any ideas ? :confused:
Sorry.. I thought about it, but forgot when I posted #-o
The error message is about having two identical entries for a same repo in your source.list. When you upgraded to hardy the first time around, the last three lines were added. Changing gutsy --> hardy made them duplicates (you already had them for gusty..)

There are two solutions, either one is fine.
1- you comment the last 3 lines in your sources.list file (add a # at the beginning)
2- replace _everything_ with my own sources.list:
```
## General.
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

## Major bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## Security.
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

```

Then run again:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Cap'n Redbeard on 2008-05-04
Ok, done that. Used your sources.list.

Now sudo apt-file update:

> redbeard@Redbeard-desktop:~$ sudo apt-file update
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz) (404)
redbeard@Redbeard-desktop:~$ 

Thanks for that. i'll try "apt-file search" and see if anything turns up. :)

---

### Post by Cap'n Redbeard on 2008-05-04
Hi bapoumba,

Interesting. Gosh, there are a lot of files out there with "gtk" in the name !

> redbeard@Redbeard-desktop:~$ apt-file search gtk+-2
libgtk-directfb-2.0-dev: /usr/lib/pkgconfig/libgtk-directfb-2.0-0/gtk+-2.0.pc
libgtk2.0-dev: /usr/lib/pkgconfig/gtk+-2.0.pc
lsb-build-desktop3: /usr/lib/lsb3/pkgconfig/gtk+-2.0.pc
valac: /usr/share/vala/vapi/gtk+-2.0.deps
valac: /usr/share/vala/vapi/gtk+-2.0.vapi
redbeard@Redbeard-desktop:~$ sudo apt-get install gtk+-2.0.pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gtk+-2.0.pc
redbeard@Redbeard-desktop:~$ 


Any idea what i'm doing wrong ? :)

---

### Post by bapoumba on 2008-05-06
gtk+-2.0.pc is not a package in hardy repos. I'm not sure I see what you are trying to do :)

---

