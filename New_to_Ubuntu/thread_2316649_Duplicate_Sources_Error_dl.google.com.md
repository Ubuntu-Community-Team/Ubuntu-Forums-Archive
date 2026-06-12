---
title: "Duplicate Sources Error dl.google.com"
date: 2016-03-09
forum: New to Ubuntu
---

### Post by marc.lavry on 2016-03-09
I've been trying to run ```
sudo apt-get update
``` and have been getting errors.

It started out as some kind of a fetch error from google, and so I went online to find a solution.  I've tried numerous suggestions from several different websites, but now I'm stuck with the following error which I cannot seem to move past.

> W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems

Can anyone help me out?

---

### Post by Bashing-om on 2016-03-09
marc.lavry; Sure !

Let's see what it is going to take to set this situation straight .

Is this a 64 bit operating system ?
show :
```

uname -a

```
as google has dropped all support for 32 bit software.

Next is what is in all the source files ?
post back the outputs - between code tags - of terminal commands :
```

grep dl.google.com /opt/google/chrome/cron/google-chrome
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we get to the bottom of the situation.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by marc.lavry on 2016-03-09
Thanks!  OK. Here's what I've got:

```
marc@Scryer3:~$ uname -a
Linux Scryer3 3.19.0-51-generic #58-Ubuntu SMP Fri Feb 26 21:22:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

```
marc@Scryer3:~$ grep dl.google.com /opt/google/chrome/cron/google-chrome
REPOCONFIG="deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main"
REPOCONFIGREGEX="deb (\[arch=[^]]*\bamd64\b[^]]*\][[:space:]]*)?https?://dl.google.com/linux/chrome/deb/ stable main"
```

```
marc@Scryer3:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ vivid main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ vivid main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ vivid universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ vivid universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ vivid multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ vivid multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu vivid-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
    41    deb http://security.ubuntu.com/ubuntu vivid-security universe
    42    deb-src http://security.ubuntu.com/ubuntu vivid-security universe
    43    deb http://security.ubuntu.com/ubuntu vivid-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb http://archive.canonical.com/ubuntu vivid partner
    51    # deb-src http://archive.canonical.com/ubuntu vivid partner
```

```
marc@Scryer3:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list~ <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google.list <==
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google.list~ <==
deb http://dl.google.com/linux/chrome/deb/ stable main
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/pipelight-ubuntu-stable-vivid.list <==
deb http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu vivid main

==> /etc/apt/sources.list.d/virtualbox.list <==
deb http://download.virtualbox.org/virtualbox/debian vivid contrib non-free
```

---

### Post by Bashing-om on 2016-03-09
marc.lavry; Uh Huh ..

Duplicated in the 3rd party sources list.
do:
```

sudo rm /etc/apt/sources.list.d/google.list
sudo rm /etc/apt/sources.list.d/google.list~

```
where " /etc/apt/sources.list.d/google-chrome.list" is the valid source.

All else looks good. You did the necessities !

Now do:
```

sudo apt update
sudo apt upgrade

```
all finer now than a frog's hair ?
[INDENT][INDENT]all there is to it
[/INDENT][/INDENT]

---

### Post by marc.lavry on 2016-03-09
That did it.  Not getting the error anymore.  Thanks a bunch!

---

### Post by Bashing-om on 2016-03-09
marc.lavry; Good deal,

Pleased it all worked out.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread)

[INDENT]more fun
[/INDENT]

---

