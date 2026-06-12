---
title: "software updater"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by anbu-s on 2015-01-12
When I check for software updates on my ubuntu laptop, it says i've the updates available (screenshot attached)

When i click on update, I get teh following error msg

Package system is broken
Check if you are using third-party repositories. If so, disable them, because they are a common source of problems.
Furthermore, run the following command in a Terminal: apt-get install -f

How can I fix this?

As you can see, I'm new to Ubuntu - so I need some basic steps invloved in correcting this package error.

---

### Post by bapoumba on 2015-01-12
Please open a terminal and post the outputs of the following commands :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by anbu-s on 2015-01-12
Here is the ouptut of those commands - thanks

```
anbu@Terminatore:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main restricted
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty universe
    15    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates universe
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18    ## team, and may not be under a free licence. Please satisfy yourself as to 
    19    ## your rights to use the software. Also, please note that software in 
    20    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    21    ## security team.
    22    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty multiverse
    23    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    24    
    25    ## N.B. software from this repository may not have been tested as
    26    ## extensively as that contained in the main release, although it includes
    27    ## newer versions of some applications which may provide useful features.
    28    ## Also, please note that software in backports WILL NOT receive any review
    29    ## or updates from the Ubuntu security team.
    30    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    31    
    32    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    33    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    34    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    35    
    36    ## Uncomment the following two lines to add software from Canonical's
    37    ## 'partner' repository.
    38    ## This software is not part of Ubuntu, but is offered by Canonical and the
    39    ## respective vendors as a service to Ubuntu users.
    40    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    41    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    42    
    43    ## Uncomment the following two lines to add software from Ubuntu's
    44    ## 'extras' repository.
    45    ## This software is not part of Ubuntu, but is offered by third-party
    46    ## developers who want to ship their latest software.
    47    # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    48    # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    49    # deb [http://ppa.launchpad.net/natecarlson/maven3/ubuntu](http://ppa.launchpad.net/natecarlson/maven3/ubuntu) precise main
    50    # deb-src [http://ppa.launchpad.net/natecarlson/maven3/ubuntu](http://ppa.launchpad.net/natecarlson/maven3/ubuntu) precise main
    51    # deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main
```
```
anbu@Terminatore:~$ ls -la /etc/apt/sources.list.d
total 120
drwxr-xr-x 2 root root 4096 Jan  8 15:02 .
drwxr-xr-x 6 root root 4096 Jan  6 22:55 ..
-rw-r--r-- 1 root root   66 Jan 12 11:38 dropbox.list
-rw-r--r-- 1 root root   66 Jan 12 11:38 dropbox.list.save
-rw-r--r-- 1 root root  321 Jan 12 11:38 fta-gnome3-trusty.list
-rw-r--r-- 1 root root  321 Jan 12 11:38 fta-gnome3-trusty.list.save
-rw-r--r-- 1 root root  320 Jan 12 11:38 gnome3-team-gnome3-staging-trusty.list
-rw-r--r-- 1 root root  318 Jan 12 11:38 gnome3-team-gnome3-staging-trusty.list.save
-rw-r--r-- 1 root root  286 Jan 12 11:38 gnome3-team-gnome3-trusty.list
-rw-r--r-- 1 root root  286 Jan 12 11:38 gnome3-team-gnome3-trusty.list.save
-rw-r--r-- 1 root root  182 Jan 12 11:38 google-talkplugin.list
-rw-r--r-- 1 root root  182 Jan 12 11:38 google-talkplugin.list.save
-rw-r--r-- 1 root root   86 Jan 12 11:38 intellinuxgraphics.list
-rw-r--r-- 1 root root   86 Jan 12 11:38 intellinuxgraphics.list.save
-rw-r--r-- 1 root root  207 Jan 12 11:38 kklimonda-evo232-trusty.list
-rw-r--r-- 1 root root  207 Jan 12 11:38 kklimonda-evo232-trusty.list.save
-rw-r--r-- 1 root root  138 Jan 12 11:38 mono-xamarin.list
-rw-r--r-- 1 root root  138 Jan 12 11:38 mono-xamarin.list.save
-rw-r--r-- 1 root root  204 Jan 12 11:38 noobslab-themes-trusty.list
-rw-r--r-- 1 root root  204 Jan 12 11:38 noobslab-themes-trusty.list.save
-rw-r--r-- 1 root root  188 Jan 12 11:38 opera-stable.list
-rw-r--r-- 1 root root  188 Jan 12 11:38 opera-stable.list.save
-rw-r--r-- 1 root root  136 Jan 12 11:38 pipelight-stable-trusty.list
-rw-r--r-- 1 root root  136 Jan 12 11:38 pipelight-stable-trusty.list.save
-rw-r--r-- 1 root root  134 Jan 12 11:38 pi-rho-security-trusty.list
-rw-r--r-- 1 root root  134 Jan 12 11:38 pi-rho-security-trusty.list.save
-rw-r--r-- 1 root root  150 Jan 12 11:38 staticfloat-julia-deps-trusty.list
-rw-r--r-- 1 root root  150 Jan 12 11:38 staticfloat-julia-deps-trusty.list.save
-rw-r--r-- 1 root root  158 Jan 12 11:38 staticfloat-julianightlies-trusty.list
-rw-r--r-- 1 root root  158 Jan 12 11:38 staticfloat-julianightlies-trusty.list.save
```
```
anbu@Terminatore:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main

==> /etc/apt/sources.list.d/fta-gnome3-trusty.list <==
# deb [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main

==> /etc/apt/sources.list.d/fta-gnome3-trusty.list.save <==
# deb [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-staging-trusty.list <==
# deb [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-staging-trusty.list.save <==
deb [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-trusty.list <==
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-trusty.list.save <==
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main

==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

==> /etc/apt/sources.list.d/intellinuxgraphics.list <==
deb [https://download.01.org/gfx/ubuntu/14.04/main](https://download.01.org/gfx/ubuntu/14.04/main) trusty main #Intel Graphics drivers

==> /etc/apt/sources.list.d/intellinuxgraphics.list.save <==
deb [https://download.01.org/gfx/ubuntu/14.04/main](https://download.01.org/gfx/ubuntu/14.04/main) trusty main #Intel Graphics drivers

==> /etc/apt/sources.list.d/kklimonda-evo232-trusty.list <==
deb [http://ppa.launchpad.net/kklimonda/evo232/ubuntu](http://ppa.launchpad.net/kklimonda/evo232/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/kklimonda/evo232/ubuntu](http://ppa.launchpad.net/kklimonda/evo232/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/kklimonda/evo232/ubuntu](http://ppa.launchpad.net/kklimonda/evo232/ubuntu) trusty main

==> /etc/apt/sources.list.d/kklimonda-evo232-trusty.list.save <==
deb [http://ppa.launchpad.net/kklimonda/evo232/ubuntu](http://ppa.launchpad.net/kklimonda/evo232/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/kklimonda/evo232/ubuntu](http://ppa.launchpad.net/kklimonda/evo232/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/kklimonda/evo232/ubuntu](http://ppa.launchpad.net/kklimonda/evo232/ubuntu) trusty main

==> /etc/apt/sources.list.d/mono-xamarin.list <==
deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy main
deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy-apache24-compat main

==> /etc/apt/sources.list.d/mono-xamarin.list.save <==
deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy main
deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy-apache24-compat main

==> /etc/apt/sources.list.d/noobslab-themes-trusty.list <==
deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main

==> /etc/apt/sources.list.d/noobslab-themes-trusty.list.save <==
deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main

==> /etc/apt/sources.list.d/opera-stable.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb [http://deb.opera.com/opera-stable/](http://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)



==> /etc/apt/sources.list.d/opera-stable.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb [http://deb.opera.com/opera-stable/](http://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)



==> /etc/apt/sources.list.d/pipelight-stable-trusty.list <==
deb [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.save <==
deb [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/pi-rho-security-trusty.list <==
deb [http://ppa.launchpad.net/pi-rho/security/ubuntu](http://ppa.launchpad.net/pi-rho/security/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pi-rho/security/ubuntu](http://ppa.launchpad.net/pi-rho/security/ubuntu) trusty main

==> /etc/apt/sources.list.d/pi-rho-security-trusty.list.save <==
deb [http://ppa.launchpad.net/pi-rho/security/ubuntu](http://ppa.launchpad.net/pi-rho/security/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pi-rho/security/ubuntu](http://ppa.launchpad.net/pi-rho/security/ubuntu) trusty main

==> /etc/apt/sources.list.d/staticfloat-julia-deps-trusty.list <==
# deb [http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu](http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu](http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu) trusty main

==> /etc/apt/sources.list.d/staticfloat-julia-deps-trusty.list.save <==
# deb [http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu](http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu](http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu) trusty main

==> /etc/apt/sources.list.d/staticfloat-julianightlies-trusty.list <==
# deb [http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu](http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu](http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu) trusty main

==> /etc/apt/sources.list.d/staticfloat-julianightlies-trusty.list.save <==
# deb [http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu](http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu](http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu) trusty main
anbu@Terminatore:~$
```

---

### Post by bapoumba on 2015-01-12
OK, that is quite a long list of ppas and third party repos you have here :)
I see wheezy active repos, do you remember what you installed from them ?

So please start with one of the recommendations in the first post :
```
sudo apt-get update
sudo apt-get -f install
```

Note : I have added code tags to your long outputs : [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by anbu-s on 2015-01-12
Thanks for your help
That seem to have fixed it now - even though i dont understand exactly how it got fixed with this command.???

---

### Post by bapoumba on 2015-01-13
From man apt-get :
```
 -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
```
So apt-get did find a solution to fix the broken dependencies from the packages that were triggering the error. Without your output, we cannot say more than that :)
Glad to see you fixed it, please mark your thread as solved (under Thread Tools), thanks.

---

