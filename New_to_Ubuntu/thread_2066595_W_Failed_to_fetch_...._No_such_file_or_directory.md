---
title: "W: Failed to fetch .... No such file or directory"
date: 2012-10-04
forum: New to Ubuntu
---

### Post by chacank on 2012-10-04
maybe this is a dumb question, but I am just a newbie .... so I really need your help that is experienced and proficient in linux operating system.

I faced a problem like this ::
when i run the command # apt-get update in terminal error messages appear :roll:

```

Get:437 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en [9,880 B] 
Get:438 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en [85.2 kB] 
Get:439 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en [978 B] 
Get:440 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en [30.2 kB] 
Fetched 26.0 MB in 35min 7s (12.3 kB/s)                                         
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/main/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/main/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-proposed/main/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/restricted/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/restricted/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-proposed/restricted/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/universe/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/universe/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-proposed/universe/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/multiverse/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/multiverse/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-proposed/multiverse/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/main/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/main/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-proposed/main/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-proposed/restricted/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/universe/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/universe/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-proposed/universe/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/multiverse/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-proposed/multiverse/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-proposed/multiverse/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/main/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/main/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-security/main/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/restricted/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/restricted/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-security/restricted/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/universe/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/universe/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-security/universe/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/main/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/main/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-security/main/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/restricted/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-security/restricted/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/universe/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/universe/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-security/universe/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-security/multiverse/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/main/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/main/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-updates/main/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/universe/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/universe/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-updates/universe/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/main/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/main/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-updates/main/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-updates/restricted/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/universe/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-updates/universe/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/main/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/main/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise/main/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/restricted/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/restricted/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise/restricted/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/universe/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/universe/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise/universe/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/multiverse/binary-amd64/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise/multiverse/binary-amd64/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/main/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise/main/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/restricted/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/restricted/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise/restricted/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/universe/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/universe/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise/universe/binary-i386/Packages: No such file or directory  ' 
 
W: Failed to fetch [ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/multiverse/binary-i386/Packages](ftp://ftp.itb.ac.id/pub/ubuntu/dists/precise/multiverse/binary-i386/Packages)  Unable to fetch file, server said 'Can't open /pub/ubuntu/dists/precise/multiverse/binary-i386/Packages: No such file or directory  ' 
 
E: Some index files failed to download. They have been ignored, or old ones used instead.
```


any solutions for me ....?
please .... [-o<

---

### Post by mathfreak123 on 2012-10-05
Judging from [ftp://ftp.itb.ac.id/pub/ubuntu/](ftp://ftp.itb.ac.id/pub/ubuntu/), it looks like whoever's running that server just removed all the ubuntu directories. You might want to try removing the site that's causing you this trouble from your software sources.

If you added this repository yourself, you can disable it like so:

System -> Administration -> Software Sources: Click "Other Software" tab and uncheck the offending repos. :D

---

### Post by NikTh on 2012-10-05
Hi , 

open a terminal and give the results of this command 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
``` 

**Please** put the results between the brackets **[noparse]```
Here
```[/noparse]** so can be readable. 

Thanks

---

### Post by chacank on 2012-10-05
> **mathfreak123 said:**
> Judging from [ftp://ftp.itb.ac.id/pub/ubuntu/](ftp://ftp.itb.ac.id/pub/ubuntu/), it looks like whoever's running that server just removed all the ubuntu directories. You might want to try removing the site that's causing you this trouble from your software sources.

If you added this repository yourself, you can disable it like so:

System -> Administration -> Software Sources: Click "Other Software" tab and uncheck the offending repos. :D
thanks for your quick response ..
I also have tried ..

chacank@chacank-K84L:~$ sudo apt-get ubuntu-restricted-extras
E: Invalid operation ubuntu-restricted-extras

whether this is also caused by the site ..?
what should I do to solve this problem ..?

help me please .... :'(

---

### Post by chacank on 2012-10-05
> **NikTh said:**
> Hi , 

open a terminal and give the results of this command 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
``` 

**Please** put the results between the brackets **[noparse]```
Here
```[/noparse]** so can be readable. 

Thanks
this is the result ..
thanks for your kindness .. :)

```
chacank@chacank-K84L:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
     5    
     6    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7    # newer versions of the distribution.
     8    deb http://archive.ubuntu.com/ubuntu precise main restricted
     9    deb-src http://archive.ubuntu.com/ubuntu precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
    14    deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb http://archive.ubuntu.com/ubuntu precise universe
    20    deb-src http://archive.ubuntu.com/ubuntu precise universe
    21    deb http://archive.ubuntu.com/ubuntu precise-updates universe
    22    deb-src http://archive.ubuntu.com/ubuntu precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    
    30    
    31    
    32    
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    deb http://archive.ubuntu.com/ubuntu precise-backports restricted main multiverse universe
    39    deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
    40    
    41    deb http://archive.ubuntu.com/ubuntu precise-security main restricted
    42    deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
    43    deb http://archive.ubuntu.com/ubuntu precise-security universe
    44    deb-src http://archive.ubuntu.com/ubuntu precise-security universe
    45    
    46    
    47    ## Uncomment the following two lines to add software from Canonical's
    48    ## 'partner' repository.
    49    ## This software is not part of Ubuntu, but is offered by Canonical and the
    50    ## respective vendors as a service to Ubuntu users.
    51    deb http://archive.canonical.com/ubuntu precise partner
    52    deb-src http://archive.canonical.com/ubuntu precise partner
    53    
    54    ## This software is not part of Ubuntu, but is offered by third-party
    55    ## developers who want to ship their latest software.
    56    deb http://extras.ubuntu.com/ubuntu precise main
    57    deb-src http://extras.ubuntu.com/ubuntu precise main
    58    
    59    deb ftp://ftp.itb.ac.id/pub/ubuntu/ precise-proposed main restricted universe multiverse
    60    deb ftp://ftp.itb.ac.id/pub/ubuntu/ precise-security main restricted universe multiverse
    61    deb ftp://ftp.itb.ac.id/pub/ubuntu/ precise-updates main restricted universe multiverse
    62    deb ftp://ftp.itb.ac.id/pub/ubuntu/ precise main restricted universe multiverse
    63    deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main universe

/etc/apt/sources.list.d/medibuntu.list

     1    ## Please report any bug on https://bugs.launchpad.net/medibuntu/
     2    deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
     3    deb-src http://packages.medibuntu.org/ precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"

/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list

     1    deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
     2    deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
```

---

### Post by newb85 on 2012-10-05
> **chacank said:**
> thanks for your quick response ..
I also have tried ..

chacank@chacank-K84L:~$ sudo apt-get ubuntu-restricted-extras
E: Invalid operation ubuntu-restricted-extras

whether this is also caused by the site ..?
what should I do to solve this problem ..?

help me please .... :'(

Probably an independent problem.
The command should be 
```
sudo apt-get **install** ubuntu-restricted-extras
```

---

### Post by NikTh on 2012-10-05
Hi , 

try these codes 
```
sudo sed -i 's/deb ftp/#deb ftp/g' /etc/apt/sources.list
```Then
```
sudo apt-get update 
sudo apt-get dist-upgrade 
```**Tip: **Precise-proposed updates are dangerous . Can do a system unstable. You can remove them if you want by => Update-Manager > Settings > Pre-released Updates (Precise-proposed) > Un-tick the box.

Thanks

---

### Post by chacank on 2012-10-05
> **NikTh said:**
> Hi , 

try these codes 
```
sudo sed -i 's/deb ftp/#deb ftp/g' /etc/apt/sources.list
```Then
```
sudo apt-get update 
sudo apt-get dist-upgrade 
```**Tip: **Precise-proposed updates are dangerous . Can do a system unstable. You can remove them if you want by => Update-Manager > Settings > Pre-released Updates (Precise-proposed) > Un-tick the box.

Thanks
after I run the code you provided
i still encountered some error messages .. :(

sudo sed -i 's/deb ftp/#deb ftp/'g /etc/apt/sources.list
sudo apt-get update

```
Hit http://archive.ubuntu.com precise-security/restricted Translation-en                                                                        
Hit http://archive.ubuntu.com precise-security/universe Translation-en                                                                          
Fetched 1,729 kB in 1min 39s (17.4 kB/s)                                                                                                        
W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US  Unable to connect to packages.medibuntu.org:http: 
 
W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en  Unable to connect to packages.medibuntu.org:http: 
 
W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US  Unable to connect to packages.medibuntu.org:http: 
 
W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en  Unable to connect to packages.medibuntu.org:http: 
 
E: Some index files failed to download. They have been ignored, or old ones used instead. 
```

what should i do now ..?

and what is causing the error ..??
whether there should be a file or something i need to delete it ....????

please help me solve this problem ..

---

### Post by NikTh on 2012-10-05
Try 

```
sudo rm /var/lib/apt/lists/* -vf 
sudo apt-key update 
sudo apt-get update
```

Thanks

---

### Post by chacank on 2012-10-05
there are still failures .... ](*,)

```
chacank@chacank-K84L:~$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for chacank: 
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/lock'
removed `/var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_binary-amd64_Packages'
removed `/var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_binary-i386_Packages'
removed `/var/lib/apt/lists/packages.medibuntu.org_dists_precise_free_source_Sources'
removed `/var/lib/apt/lists/packages.medibuntu.org_dists_precise_InRelease'
removed `/var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-amd64_Packages'
removed `/var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_binary-i386_Packages'
removed `/var/lib/apt/lists/packages.medibuntu.org_dists_precise_non-free_source_Sources'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_precise_Release.gpg'
chacank@chacank-K84L:~$ sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
chacank@chacank-K84L:~$ sudo apt-get update
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://extras.ubuntu.com precise InRelease                                 
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]           
Ign http://archive.ubuntu.com precise InRelease                                
Get:2 http://packages.medibuntu.org precise InRelease [7,096 B]      
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://archive.ubuntu.com precise-updates InRelease                        
Get:4 http://ppa.launchpad.net precise Release [11.9 kB]                   
Ign http://archive.ubuntu.com precise-backports InRelease                      
Get:5 http://extras.ubuntu.com precise Release [11.9 kB]                       
Ign http://archive.ubuntu.com precise-security InRelease                       
Get:6 http://archive.ubuntu.com precise Release.gpg [198 B]               
Get:7 http://packages.medibuntu.org precise/free Sources [3,348 B]             
Get:8 http://ppa.launchpad.net precise/main Sources [2,954 B]                  
Get:9 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:10 http://archive.ubuntu.com precise-backports Release.gpg [198 B]         
Get:11 http://ppa.launchpad.net precise/main amd64 Packages [4,175 B]          
Get:12 http://archive.ubuntu.com precise-security Release.gpg [198 B]          
Get:13 http://extras.ubuntu.com precise/main Sources [7,352 B]                 
Get:14 http://archive.ubuntu.com precise Release [49.6 kB]                     
Get:15 http://ppa.launchpad.net precise/main i386 Packages [4,155 B]           
Get:16 http://packages.medibuntu.org precise/non-free Sources [4,410 B]        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:17 http://extras.ubuntu.com precise/main amd64 Packages [9,655 B]          
Get:18 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Get:19 http://packages.medibuntu.org precise/free amd64 Packages [3,237 B]     
Get:20 http://extras.ubuntu.com precise/main i386 Packages [9,654 B]           
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:21 http://archive.ubuntu.com precise-backports Release [49.6 kB]           
Get:22 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Get:23 http://packages.medibuntu.org precise/non-free amd64 Packages [6,049 B] 
Get:24 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Get:25 http://packages.medibuntu.org precise/free i386 Packages [3,243 B]      
Get:26 http://packages.medibuntu.org precise/non-free i386 Packages [6,636 B]  
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:27 http://archive.ubuntu.com precise/main Sources [934 kB]                 
Ign http://packages.medibuntu.org precise/free TranslationIndex               
Ign http://packages.medibuntu.org precise/non-free TranslationIndex           
Err http://packages.medibuntu.org precise/free Translation-en_US               
  Unable to connect to packages.medibuntu.org:http:
Err http://packages.medibuntu.org precise/free Translation-en                  
  Unable to connect to packages.medibuntu.org:http:
Err http://packages.medibuntu.org precise/non-free Translation-en_US           
  Unable to connect to packages.medibuntu.org:http:
Err http://packages.medibuntu.org precise/non-free Translation-en              
  Unable to connect to packages.medibuntu.org:http:
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:28 http://archive.ubuntu.com precise/restricted Sources [5,470 B]          
Get:29 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Get:30 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Get:31 http://archive.ubuntu.com precise/main amd64 Packages [1,273 kB]        
Get:32 http://archive.ubuntu.com precise/main amd64 Packages [1,273 kB]        
Get:33 http://archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]   
Get:34 http://archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]    
Get:35 http://archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]    
Get:36 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:37 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:38 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:39 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:40 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:41 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]       
Get:42 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B] 
Get:43 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]   
Get:44 http://archive.ubuntu.com precise-updates/main Sources [172 kB]         
Get:45 http://archive.ubuntu.com precise-updates/restricted Sources [3,285 B]  
Get:46 http://archive.ubuntu.com precise-updates/universe Sources [58.0 kB]    
Get:47 http://archive.ubuntu.com precise-updates/main amd64 Packages [397 kB]  
Get:48 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [6,755 B]
Get:49 http://archive.ubuntu.com precise-updates/universe amd64 Packages [143 kB]
Get:50 http://archive.ubuntu.com precise-updates/main i386 Packages [403 kB]   
Get:51 http://archive.ubuntu.com precise-updates/main i386 Packages [403 kB]   
Get:52 http://archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:53 http://archive.ubuntu.com precise-updates/universe i386 Packages [143 kB]
Get:54 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:55 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:56 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:57 http://archive.ubuntu.com precise-backports/main Sources [2,422 B]      
Get:58 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]   
Get:59 http://archive.ubuntu.com precise-backports/universe Sources [15.1 kB]  
Get:60 http://archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:61 http://archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:62 http://archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:63 http://archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:64 http://archive.ubuntu.com precise-backports/universe amd64 Packages [13.7 kB]
Get:65 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:66 http://archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:67 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Get:68 http://archive.ubuntu.com precise-backports/universe i386 Packages [13.7 kB]
Get:69 http://archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:70 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:71 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:72 http://archive.ubuntu.com precise-backports/universe TranslationIndex [72 B]
Get:73 http://archive.ubuntu.com precise-security/main Sources [49.1 kB]       
Get:74 http://archive.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:75 http://archive.ubuntu.com precise-security/universe Sources [14.5 kB]   
Get:76 http://archive.ubuntu.com precise-security/main amd64 Packages [173 kB] 
Get:77 http://archive.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:78 http://archive.ubuntu.com precise-security/universe amd64 Packages [48.4 kB]
Get:79 http://archive.ubuntu.com precise-security/main i386 Packages [179 kB]  
Get:80 http://archive.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:81 http://archive.ubuntu.com precise-security/universe i386 Packages [48.6 kB]
Get:82 http://archive.ubuntu.com precise-security/main TranslationIndex [73 B] 
Get:83 http://archive.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:84 http://archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:85 http://archive.ubuntu.com precise/main Translation-en [726 kB]          
Get:86 http://archive.ubuntu.com precise/main Translation-en [726 kB]          
Get:87 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]   
Get:88 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]    
Get:89 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]    
Get:90 http://archive.ubuntu.com precise-updates/main Translation-en [196 kB]  
Get:91 http://archive.ubuntu.com precise-updates/restricted Translation-en [1,484 B]
Get:92 http://archive.ubuntu.com precise-updates/universe Translation-en [83.8 kB]
Get:93 http://archive.ubuntu.com precise-backports/main Translation-en [1,244 B]
Get:94 http://archive.ubuntu.com precise-backports/multiverse Translation-en [1,476 B]
Get:95 http://archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:96 http://archive.ubuntu.com precise-backports/universe Translation-en [9,880 B]
Get:97 http://archive.ubuntu.com precise-security/main Translation-en [85.2 kB]
Get:98 http://archive.ubuntu.com precise-security/restricted Translation-en [978 B]
Get:99 http://archive.ubuntu.com precise-security/universe Translation-en [30.2 kB]
Fetched 4,199 kB in 5min 28s (12.8 kB/s)                                       
W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en  Unable to connect to packages.medibuntu.org:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.
chacank@chacank-K84L:~$ 
```

if i ignore the message and does not affect the system or the software on my computer....  :confused:

---

### Post by NikTh on 2012-10-05
We can easily vanish these messages by deleting the medibuntu.list . The strange here is that I tested the sources and worked fine on me. 

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
above command will delete the medibuntu addition from your sources.list and will vanish the errors. 
```
sudo apt-get update
```
You can add the source again if you want.

---

### Post by chacank on 2012-10-06
thank you very much .. :D

my problem is solved for your help .... NikTh. =D>

---

