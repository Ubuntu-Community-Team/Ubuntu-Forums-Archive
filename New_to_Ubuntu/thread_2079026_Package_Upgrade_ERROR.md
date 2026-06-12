---
title: "Package Upgrade ERROR"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-11-01
Hi Community:

I'm running 12.04.1 and upgrated from 10.04 using the automatic upgrade route... I just clicked a button and the system upgraded nicely.

Now, 3 months later I'm getting errors when my system wants to upgrade packages automatically.... It wants me to insert a CD for Quetzal.

What is this all about??

How do I upgrade my packages without getting this error... usins Synaptic doesn't work.

Thanks,
Old Jimma

---

### Post by monkeybrain2012 on 2012-11-01
The update manager is configured by default to prompt you to upgrade to a new release when one is available. You probably have clicked yes at some point and it now wants to upgrade to 12.10. I think this 'feature' is dangerous to inexperienced users and even experienced users not paying attention. I always disable it from upgrade manager's setting when I install Ubuntu (check never for distro upgrade) 

Now this is an explanation to what happened, but unfortunately I don't know how to fix it. That happened to me once when I was a new user, I ended up having to reinstall the system. I hope someone will show you a better way.

---

### Post by NikTh on 2012-11-01
Hi , 
please open a terminal (CTRL+ALT+T) and give the results of bellow commands.
You can copy-paste the commands from here to terminal and vise versa (for the results)

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
``````
lsb_release -rcd ; uname -r
```Put the results between these brackets **[noparse]```
here
```[/noparse]** in order to be easier to read. 

Thanks

---

### Post by ibjsb4 on 2012-11-01
Is CDrom unchecked?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by Old Jimma on 2012-11-03
```

/etc/apt/sources.list

     1	# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
     2	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3	# newer versions of the distribution.
     4	
     5	deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ dists/quantal/main/binary-i386/
     6	deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ dists/quantal/multiverse/binary-i386/
     7	deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ dists/quantal/restricted/binary-i386/
     8	deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ dists/quantal/universe/binary-i386/
     9	deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
    10	deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
    11	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
    12	deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    13	deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    14	
    15	## Major bug fix updates produced after the final release of the
    16	## distribution.
    17	deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    18	deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    21	## team. Also, please note that software in universe WILL NOT receive any
    22	## review or updates from the Ubuntu security team.
    23	deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    24	deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    25	deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    26	deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    27	
    28	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    29	## team, and may not be under a free licence. Please satisfy yourself as to
    30	## your rights to use the software. Also, please note that software in
    31	## multiverse WILL NOT receive any review or updates from the Ubuntu
    32	## security team.
    33	deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    34	deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    35	deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    36	deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    37	
    38	## Uncomment the following two lines to add software from the 'backports'
    39	## repository.
    40	## N.B. software from this repository may not have been tested as
    41	## extensively as that contained in the main release, although it includes
    42	## newer versions of some applications which may provide useful features.
    43	## Also, please note that software in backports WILL NOT receive any review
    44	## or updates from the Ubuntu security team.
    45	# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    46	# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
    47	
    48	## Uncomment the following two lines to add software from Canonical's
    49	## 'partner' repository.
    50	## This software is not part of Ubuntu, but is offered by Canonical and the
    51	## respective vendors as a service to Ubuntu users.
    52	deb http://archive.canonical.com/ubuntu precise partner
    53	# deb-src http://archive.canonical.com/ubuntu lucid partner
    54	
    55	deb http://security.ubuntu.com/ubuntu precise-security main restricted
    56	deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    57	deb http://security.ubuntu.com/ubuntu precise-security universe
    58	deb-src http://security.ubuntu.com/ubuntu precise-security universe
    59	deb http://security.ubuntu.com/ubuntu precise-security multiverse
    60	deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    61	
    62	

/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list

     1	deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
     2	deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main

/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list

     1	deb http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
     2	deb-src http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main

/etc/apt/sources.list.d/mozillateam-firefox-stable-lucid.list

     1	# deb http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu precise main # disabled on upgrade to precise

/etc/apt/sources.list.d/medibuntu.list

     1	## Please report any bug on https://bugs.launchpad.net/medibuntu/
     2	deb http://packages.medibuntu.org/ precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
     3	# deb-src http://packages.medibuntu.org/ precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"

/etc/apt/sources.list.d/google-talkplugin.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	deb http://dl.google.com/linux/talkplugin/deb/ stable main

/etc/apt/sources.list.d/ricotz-testing-precise.list

     1	deb http://ppa.launchpad.net/ricotz/testing/ubuntu precise main
     2	deb-src http://ppa.launchpad.net/ricotz/testing/ubuntu precise main

/etc/apt/sources.list.d/ubuntu-audio-dev-ppa-precise.list

     1	deb http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu precise main
     2	deb-src http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu precise main

/etc/apt/sources.list.d/dropbox.list

     1	# deb http://linux.dropbox.com/ubuntu precise main # disabled on upgrade to precise

/etc/apt/sources.list.d/openoffice-pkgs-ppa-lucid.list

     1	# deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu precise main # disabled on upgrade to precise


```

---

### Post by howefield on 2012-11-03
Comment out the lines referring to the Quantal CD, lines 5 to 10 inclusive.

---

### Post by NikTh on 2012-11-03
Do as @howefield suggested. I don't know where did you find these lines , it seems like you loaded Lubuntu 12.10 CD/DVD/USB or something. 

From terminal give 
```
gksudo gedit /etc/apt/sources.list
``` 

and place a comment (this symbol #) at the beginning of these 6 lines 
```

     5	deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ dists/quantal/main/binary-i386/
     6	deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ dists/quantal/multiverse/binary-i386/
     7	deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ dists/quantal/restricted/binary-i386/
     8	deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ dists/quantal/universe/binary-i386/
     9	deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
    10	deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
```
then save the document and run in terminal 
```
sudo apt-get update 
sudo apt-get dist-upgrade
``` 

and should be smooth. 

Thanks

---

### Post by Old Jimma on 2012-11-03
Thanks to howfield and NikTH for solving this!

THeir soluiton worked!

Thanks!

Old Jimma

ps... I didn't do anything to put those lines there... All I did was to do an automatic upgrade from 10.04 to 12.04.1

---

