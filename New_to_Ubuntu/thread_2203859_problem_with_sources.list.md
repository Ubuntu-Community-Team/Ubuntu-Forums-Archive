---
title: "problem with sources.list"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by robertasbalt on 2014-02-05
Hi, I am new in using Ubuntu system and encountered my first problem. 
The problem is when I try to update or install something using "sudo apt-get" with terminal
i get this error mesage:
E: Malformed line 1 in source list /etc/apt/sources.list.d/opera.list (dist parse)
E: The list of sources could not be read.
and this is what I have when i print out sources.list in terminal:
     1    # deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted 
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy main restricted
     6    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
    11    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy universe
    17    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy universe
    18    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates universe
    19    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy multiverse
    27    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy multiverse
    28    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates multiverse
    29    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse
    37    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse
    38    
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
    51    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
So can some help to solve this problem?

---

### Post by papibe on 2014-02-05
Hi robertasbalt. Welcome to the forum ):P

From the error message, it looks like the problem may lay on another file inside the sources.list.d directory. It would be very useful to take a look at all your sources files.

Could you open a terminal, run this command, and post back its results?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by Dave_L on 2014-02-05
The error message is referring to this file: /etc/apt/sources.list.d/opera.list

If you can't identify the problem with the file, post it here. Please enclose it in [ code ] ... [ /code ] tags (without the spaces).

---

### Post by robertasbalt on 2014-02-05
This is the list I have got after entering this code:
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
List:
```

[B]/etc/apt/sources.list.d/webupd8team-java-saucy.list

     1    deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) saucy main
     2    # deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) saucy main

/etc/apt/sources.list.d/skype.list

     1    deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free #Repository for Skype (stable)

/etc/apt/sources.list.d/opera.list

     1    deb [http://deb.opera.com/stable](http://deb.opera.com/stable) non-free

/etc/apt/sources.list.d/tualatrix-ppa-saucy.list

     1    deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) saucy main
     2    # deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) saucy main

/etc/apt/sources.list.d/atareao-atareao-saucy.list

     1    deb [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) saucy main
     2    # deb-src [http://ppa.launchpad.net/atareao/atareao/ubuntu](http://ppa.launchpad.net/atareao/atareao/ubuntu) saucy main

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted 
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy main restricted
     6    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
    11    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy universe
    17    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy universe
    18    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates universe
    19    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy multiverse
    27    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy multiverse
    28    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates multiverse
    29    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse
    37    deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse
    38    
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
    51    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
[/B]
```

---

### Post by papibe on 2014-02-05
Thanks.

You missed the word stable on the opera file:
```

/etc/apt/sources.list.d/opera.list

     1    deb http://deb.opera.com/stable non-free

```
Open an editor like this:
```
gksudo gedit /etc/apt/sources.list.d/opera.list
```
and edit the file so it looks like this:
```
deb http://deb.opera.com/stable **stable** non-free
```
Save the file, and try again updating your sources with apt-get.

Hope it helps. Let us know how it goes.
Regards.

EDIT1: take a look at this tutorial: [Opera Browser]("https://help.ubuntu.com/community/OperaBrowser"). You may need to add a GPG key before you can actually update your sources.

---

### Post by robertasbalt on 2014-02-05
Everything work and fixed the problem, thank's man for the help :)

---

