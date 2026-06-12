---
title: "Cannot get past system updates check"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by richlion2 on 2015-04-27
Hello, 

I've got Kubuntu on an HP Compaq 8510w with an Nvidia graphics card. 
I seem to stuck in a loop in the updates. When Muon starts its says I have new packages to install.
Then it says mys system update is more than a week ago, "please run Check for updates".
When I run I crash in the errors:
> 
Can't locate these packages -
 [http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)
 404  Not Found
 

 [http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)
 404  Not Found


I attached screenshot.

I read some instructions that I should run :
sudo apt-get dist-upgrade
sudo apt-get update

This still doesn't help and I cannot get passed that error.

Any hints?

Thanks
Richard

---

### Post by Vladlenin5000 on 2015-04-27
Those PPAs no longer exist, hence the errors.
Remove them then run _in this exact order_: ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade (optional)
```

---

### Post by Bashing-om on 2015-04-27
richlion2; Hey ...

ninja'd by Vladlenin5000; but my validation:

per:
[http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/](http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/)
raring was the last supported release from this PPA.
In Software Center disable this PPA .

now see what results;
terminal commands:
```

sudo apt-gt update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

[INDENT][INDENT]? finer than a frog's hair 
[/INDENT][/INDENT]

---

### Post by richlion2 on 2015-04-28
This command:
> 
sudo apt-get update


shows these errors:
```

: Nie uda&#322;o si&#281; pobra&#263; http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Nie uda&#322;o si&#281; pobra&#263; http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Nie uda&#322;o si&#281; pobra&#263; niektórych plików indeksu, zosta&#322;y one zignorowane lub u&#380;yto ich starszej wersji.



```

How should I proceed?

I am interested  in why the Muon updater does handle this situation? 
I am preparing a laptop for someone who has no clue about an operating system, so I need to make sure I provide support and the updates will not come to a dead end like I had with other distros.

Thanks

---

### Post by Geoffrey_Arndt on 2015-04-28
If you are going to support a linux distro, then it would be smart of you to make sure :

>  That you are using an LTS version (with support for 5 years from release date),
>  That your "Sources List" is correct (and stays correct . . only you can change it),
>  IF you do not FULLY understand the concepts of official repositories and sources . . please read up on that . . only add PPA's from trusted sources and that exactly match the release version (e.g., 14.04.2 "Trusty")
>  Also, recognize each source may be a different physical server also (and url), and could be temporarily "down" at any time . . .often a good idea is to  check "choose best server" from time to time in your updater app

So, perhaps an full edit of Sources tab in the updater (or in /etc/sources) will reveal what needs to be removed.

---

### Post by Bashing-om on 2015-04-28
richlion2; Good Morning .


+1 to Geoffrey_Arndt's recommendations.

Looks as there is yet another PPA that might be unsupported ..:
> 
How should I proceed?

I am interested in why the Muon updater does handle this situation? 
I am preparing a laptop for someone who has no clue about an operating system, so I need to make sure I provide support and the updates will not come to a dead end like I had with other distros.How should I proceed?



Package management is a system in it's own right, and yes it can get rather deep and complex. This is the reference I still use:
[https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites).

How do we proceed - we check the source list file(S) and see what the system is directing to fetch and from where.

To aid you in this determination, post back - Between code tags, please - the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Get the source(s) list(S) correct for the applications, system then updated and the installed packages upgraded to what is current , Turn the box over to your client .

[INDENT][INDENT]1 2 3 
[/INDENT][/INDENT]

---

### Post by richlion2 on 2015-05-06
Hello, 

thanks for all your patience, since I am new to Ubuntu I know I need to learn how the packaging system and there are a lot of new terms I am not familiar with. 

In the meantime, here are the contents you requested:

```

$ cat  -n /etc/apt/sources.list
     1  # deb cdrom:[Kubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.1)]/ trusty main multiverse restricted universe
     2
     3  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4  # newer versions of the distribution.
     5  deb http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted
     6  deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty main restricted
     7
     8  ## Major bug fix updates produced after the final release of the
     9  ## distribution.
    10  deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11  deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12
    13  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14  ## team. Also, please note that software in universe WILL NOT receive any
    15  ## review or updates from the Ubuntu security team.
    16  deb http://pl.archive.ubuntu.com/ubuntu/ trusty universe
    17  deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty universe
    18  deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19  deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22  ## team, and may not be under a free licence. Please satisfy yourself as to 
    23  ## your rights to use the software. Also, please note that software in 
    24  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25  ## security team.
    26  deb http://pl.archive.ubuntu.com/ubuntu/ trusty multiverse
    27  deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty multiverse
    28  deb http://pl.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29  deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30
    31  ## N.B. software from this repository may not have been tested as
    32  ## extensively as that contained in the main release, although it includes
    33  ## newer versions of some applications which may provide useful features.
    34  ## Also, please note that software in backports WILL NOT receive any review
    35  ## or updates from the Ubuntu security team.
    36  deb http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37  deb-src http://pl.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38
    39  deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40  deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted                                                          
    41  deb http://security.ubuntu.com/ubuntu trusty-security universe                                                                     
    42  deb-src http://security.ubuntu.com/ubuntu trusty-security universe                                                                 
    43  deb http://security.ubuntu.com/ubuntu trusty-security multiverse                                                                   
    44  deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse                                                               
    45                                                                                                                                     
    46  ## Uncomment the following two lines to add software from Canonical's                                                              
    47  ## 'partner' repository.                                                                                                                
    48  ## This software is not part of Ubuntu, but is offered by Canonical and the                                                                
    49  ## respective vendors as a service to Ubuntu users.                                                                                        
    50  deb http://archive.canonical.com/ubuntu trusty partner                                                                                     
    51  # deb-src http://archive.canonical.com/ubuntu trusty partner                                                                                
    52                                                                                                                                              
    53  ## This software is not part of Ubuntu, but is offered by third-party                                                                        
    54  ## developers who want to ship their latest software.                                                                                        
    55  deb http://extras.ubuntu.com/ubuntu trusty main
    56  deb-src http://extras.ubuntu.com/ubuntu trusty main
krysia@Paderewski:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/disper-dev-ppa-trusty.list <==
deb http://ppa.launchpad.net/disper-dev/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/disper-dev/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/disper-dev-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/disper-dev/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/disper-dev/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
krysia@Paderewski:~$ 


```

Thanks again, 
Richard

---

### Post by Bashing-om on 2015-05-06
richlion2; Hello;

Hey, It is all a process of learning and picking up on linux is akin to learning a new language -> patience is a virtue and you only get out of it what you put into it.
In this case the patience thing is finding the cause of the package manager's discontent.
That 2nd PPA that the Package manager is screaming and hollering about:
> 
deb [http://ppa.launchpad.net/disper-dev/ppa/ubuntu](http://ppa.launchpad.net/disper-dev/ppa/ubuntu) trusty main

Let's look at what it is trying to fetch:
in your browser:
```

http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/

```
you see there is no listing for trusty. Thus the system is unable again to comply.

Disable this source also.

Now let's see what the status is:
```

sudo apt-get update
sudo apt-get upgrade

```
I do expect there to be new kernels available for install in that output . If so we deal with the "held packages" when the system is stable.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by richlion2 on 2015-05-11
Thank you so much for helping. I did manage to remove those from the repository using Muon (brilliant !!!! ) 

Update and Upgrade now works.


I may have found the source of my problems. 
I search on how to play blue-ray discs with VLC and came up with instructions on this like that may be out of date:
[http://askubuntu.com/questions/140080/playing-blu-ray-using-vlc](http://askubuntu.com/questions/140080/playing-blu-ray-using-vlc)

The fist two instructions are giving me a warning that the sources are for upcoming releases:
```

rysiek@richlion9:~$ sudo add-apt-repository ppa:videolan/stable-daily
 This PPA contains daily builds from the latest VLC maintenance branch.

This PPA is used for test building new and upcoming point releases of VLC that can get into Ubuntu through stable release updates (SRU) or security updates. You don't find major version updates in this PPA (e.g. no update from 2.1.x to 2.2.x).
 More info: https://launchpad.net/~videolan/+archive/ubuntu/stable-daily
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmppqrinub1/secring.gpg' created
gpg: keyring `/tmp/tmppqrinub1/pubring.gpg' created
gpg: requesting key 801DF724 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmppqrinub1/trustdb.gpg: trustdb created
gpg: key 801DF724: public key "Launchpad Daily Build of master branch" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK


```

But then I get errors when running sudo apt-get update:
```

Get:33 http://ppa.launchpad.net trusty/main Translation-en [1,978 B]           
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Fetched 2,947 kB in 13s (213 kB/s)                                             
W: Failed to fetch http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
rysiek@richlion9:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.


```

I think I need a more up to date version of how to install stuff for playing blue-ray, maybe someone has hints on where I can find instructions?

I found how to use SMPlayer here:
[http://ubuntuhandbook.org/index.php/2014/04/smplayer-play-blu-ray-discs/](http://ubuntuhandbook.org/index.php/2014/04/smplayer-play-blu-ray-discs/)

I am not a big fan of SMPlayer, I'd rather use VLC.

Thanks, 
Richard

---

### Post by Bashing-om on 2015-05-11
richlion2; Yuk;

You are not checking what you are doing:
PPAs are 3rd party software - not supported by ubuntu - use at your own risk, AND do your homework.
[http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu/dists/](http://ppa.launchpad.net/motumedia/mplayer-daily/ubuntu/dists/)
Has no provision for 'trusty' .
So clean up the mess, install VLC properly, and the dependencies required to utilized non-free means.

To see the status of vlc:
```

dpkg -l vlc

```
the 1st column in the output we hope is 'ii' .
If it is 'ii" then install the dependencies for non-free use of codecs:
```

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libdvdread4
sudo apt-get install libdvdcss libdvdnav4
sudo /usr/share/doc/libdvdread4/install-css.sh

```

[INDENT][INDENT]try'n to help
[INDENT][INDENT]in this process of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by walttheboss on 2015-05-11
Here are things that will get your package manager working again. 

H) Repair broken packages
I) Check and Repair
a) sudo dpkg --configure -a
II) Looks for and install missing dependencies 
a) sudo apt-get -f install
III) Sometimes the headers/sources get messed up.  
a) sudo rm /var/lib/apt/lists/* -vf
b) sudo apt-get update

---

### Post by mc4man on 2015-05-11
If you see a suggestion to run a command to add a ppa, for example the one you recently used - 
sudo add-apt-repository ppa:motumedia/mplayer-daily
I'd suggest first go to the ppa to see if it's suitable for you & whatever release of ubuntu you are on. In the case of the above you'd found it's old & has no 14.04 packages.
(- easy way to find ppa - google search, in this case just search  ppa:motumedia/mplayer-daily

Anyone suggesting a sudo add-apt-repository command should also provide a link to the ppa & suggest user go there first..

---

### Post by richlion2 on 2015-05-12
> **walttheboss said:**
> Here are things that will get your package manager working again. 

H) Repair broken packages
I) Check and Repair
a) sudo dpkg --configure -a
II) Looks for and install missing dependencies 
a) sudo apt-get -f install
III) Sometimes the headers/sources get messed up.  
a) sudo rm /var/lib/apt/lists/* -vf
b) sudo apt-get update

Thanks, my packaging system is now working. I removed the PPA stuff from the sources.

Richard

---

### Post by richlion2 on 2015-05-12
Hello, 

you are most helpful here and I want to thank you. 

Although my packaging system is now working and I ran your instructions and I also copied the file :
```

~/.config/aacs$ wget [http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg](http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg)

```

VLC is still complaining:
 [COLOR=#ff0000]```

Blu-ray error:
```[/COLOR]```

 [COLOR=#000000]No valid processing key found in AACS config file
[/COLOR]
```[COLOR=#000000]

These are the links I followed:
[http://ubuntuforums.org/showthread.php?t=1967280](http://ubuntuforums.org/showthread.php?t=1967280)
[http://ubuntuforums.org/showthread.php?t=2198588](http://ubuntuforums.org/showthread.php?t=2198588)
[http://vlc-bluray.whoknowsmy.name/](http://vlc-bluray.whoknowsmy.name/)

(this is an edit)

I can play one of my blue rays discs, but not all of them, I've got a Poirot series and it seems it is probably protected. Is there any chance I can get hold of a more up to date KEYDB.cfg file for my specific title?


Thanks, 
Richard

[/COLOR]

---

