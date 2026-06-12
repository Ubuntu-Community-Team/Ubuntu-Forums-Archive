---
title: "Duplicate Sources"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by IvoGuerreiro on 2014-03-14
Goodnight Everyone, this is my first time asking for help, so i hope doing it right
I have all this duplicated.
```

W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ saucy/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ saucy/multiverse amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ saucy/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ saucy/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ saucy/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_multiverse_binary-i386_Packages)

```
My question is, there are other way to resolve this without change my souce.list
And if its possible, can someone tell me what i did wrong to cause this?

---

### Post by papibe on 2014-03-14
Hi IvoGuerreiro.

Could you open a terminal, run this command, and post back the results (you can copy/paste the text)?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by IvoGuerreiro on 2014-03-14
Yes i can, here he goes
```

ivoguerreiro@ubuntu:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/rvm-smplayer-saucy.list

     1    deb http://ppa.launchpad.net/rvm/smplayer/ubuntu saucy main
     2    # deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu saucy main

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://pt.archive.ubuntu.com/ubuntu/ saucy main restricted
     6    deb-src http://pt.archive.ubuntu.com/ubuntu/ saucy main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://pt.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    11    deb-src http://pt.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://pt.archive.ubuntu.com/ubuntu/ saucy universe
    17    deb-src http://pt.archive.ubuntu.com/ubuntu/ saucy universe
    18    deb http://pt.archive.ubuntu.com/ubuntu/ saucy-updates universe
    19    deb-src http://pt.archive.ubuntu.com/ubuntu/ saucy-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://pt.archive.ubuntu.com/ubuntu/ saucy multiverse
    27    deb-src http://pt.archive.ubuntu.com/ubuntu/ saucy multiverse
    28    deb http://pt.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    29    deb-src http://pt.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://pt.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    37    deb-src http://pt.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu saucy-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
    41    deb http://security.ubuntu.com/ubuntu saucy-security universe
    42    deb-src http://security.ubuntu.com/ubuntu saucy-security universe
    43    deb http://security.ubuntu.com/ubuntu saucy-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu saucy partner
    51    # deb-src http://archive.canonical.com/ubuntu saucy partner
    52    
    53    ## Uncomment the following two lines to add software from Ubuntu's
    54    ## 'extras' repository.
    55    ## This software is not part of Ubuntu, but is offered by third-party
    56    ## developers who want to ship their latest software.
    57    # deb http://extras.ubuntu.com/ubuntu saucy main
    58    # deb-src http://extras.ubuntu.com/ubuntu saucy main
    59    deb http://archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse
    60    deb http://archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse
ivoguerreiro@ubuntu:~$ 

```

---

### Post by thenh813 on 2014-03-14
Do the folowing:
```

gksu gedit /etc/apt/sourcs.list

```

Coment out any duplicated lines. This really isnt a problem, its just letting you know the same line is in the sources list multiple times. Commenting out a line simply involves adding a # and a few spaces to the beginning of the unwanted line. This disables it.

You have to update the database afterwards so it removes the errors.
```

sudo apt-get update

```

If you ever want to undo the disabling, simply remove the # and spaces before the deb or deb-src lines you want to reinable and rerun sudo apt-get update.

---

### Post by papibe on 2014-03-14
Thanks.

The last two lines are duplicated:
```

    59    deb http://archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse
    60    deb http://archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse

```
Open the file like this
```
gksudo gedit /etc/apt/sources.list
```
or like this:
```
sudo nano /etc/apt/sources.list
```
and remove the last line (#60).

Then update your sources:
```
sudo apt-get update
```
That should do it.

Hope it helps. Let us know if that solved the problem.
Regards.

---

### Post by thenh813 on 2014-03-14
Ok, you posted while I was typing, edit /etc/apt/sources.list to look like this:

```


# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy main restricted

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) saucy main
deb [http://badgerports.org](http://badgerports.org) saucy main
deb-src [http://badgerports.org](http://badgerports.org) saucy main


```

@papibe I see you did too LOL.

---

### Post by IvoGuerreiro on 2014-03-14
Tks you all

Papibe that work perfectly jesus, many tks. i will try to see how you arrived to that solution.

Tks, one more time.

---

