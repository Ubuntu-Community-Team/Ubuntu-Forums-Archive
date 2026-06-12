---
title: "Can't load the repository list"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by bottaw on 2013-05-22
I just tried adding a new repository to my list to download a game and now it can't read my list at all. When I type the update command in the terminal, I receive the following message: 

E: Malformed line 66 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.


I don't know what to do and I'm really concerned. Can someone please help?

---

### Post by papibe on 2013-05-22
Hi bottaw.

Could you post the output of this command?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by claracc on 2013-05-22
could you please post your sources.list file?

In a xterm run:

cat /etc/apt/sources.list

and post the result here.

As it is said there will be " Malformed line 66 in source list /etc/apt/sources.list (dist parse)"

---

### Post by bottaw on 2013-05-22
```
/etc/apt/sources.list.d/ubuntu-unity-experimental-certified-raring.list


     1	deb [http://ppa.launchpad.net/ubuntu-unity/experimental-certified/ubuntu](http://ppa.launchpad.net/ubuntu-unity/experimental-certified/ubuntu) raring main
     2	# deb-src [http://ppa.launchpad.net/ubuntu-unity/experimental-certified/ubuntu](http://ppa.launchpad.net/ubuntu-unity/experimental-certified/ubuntu) raring main


/etc/apt/sources.list.d/steam.list


     1	# deb [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam # disabled on upgrade to raring
     2	# deb-src [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam # disabled on upgrade to raring


/etc/apt/sources.list.d/handbrake-ubuntu-ppa-quantal.list




/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list


     1	# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu) raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to raring


/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_fetchnotes_ubuntu.list


     1	# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/fetchnotes/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/fetchnotes/ubuntu) raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to raring


/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list


     1	# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu) raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to raring


/etc/apt/sources.list.d/stevenrwalter-ppa-quantal.list


     1	# deb [http://ppa.launchpad.net/stevenrwalter/ppa/ubuntu](http://ppa.launchpad.net/stevenrwalter/ppa/ubuntu) quantal main
     2	# deb-src [http://ppa.launchpad.net/stevenrwalter/ppa/ubuntu](http://ppa.launchpad.net/stevenrwalter/ppa/ubuntu) quantal main


/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_apollo_ubuntu.list


     1	# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/apollo/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/apollo/ubuntu) raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to raring


/etc/apt/sources.list.d/scopes-packagers-ppa-raring.list


     1	deb [http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu](http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu) raring main
     2	# deb-src [http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu](http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu) raring main


/etc/apt/sources.list.d/ajackson-bcs-ppa-quantal.list


     1	# deb [http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu) quantal main
     2	# deb-src [http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu](http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu) quantal main


/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_dd-panel_ubuntu.list


     1	# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/dd-panel/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/dd-panel/ubuntu) raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to raring


/etc/apt/sources.list.d/stebbins-handbrake-releases-quantal.list




/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_splashtop-client_ubuntu.list


     1	deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/splashtop-client/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/splashtop-client/ubuntu) raring main #Added by software-center; credentials stored in /etc/apt/auth.conf


/etc/apt/sources.list.d/google-chrome.list


     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	# deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_slimboat_ubuntu.list


     1	# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/slimboat/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/slimboat/ubuntu) raring main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to raring


/etc/apt/sources.list


     1	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
     2	
     3	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
     4	# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
     5	
     6	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     7	# newer versions of the distribution.
     8	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
     9	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
    10	
    11	## Major bug fix updates produced after the final release of the
    12	## distribution.
    13	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
    14	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17	## team. Also, please note that software in universe WILL NOT receive any
    18	## review or updates from the Ubuntu security team.
    19	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
    20	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
    21	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
    22	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
    23	
    24	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25	## team, and may not be under a free licence. Please satisfy yourself as to 
    26	## your rights to use the software. Also, please note that software in 
    27	## multiverse WILL NOT receive any review or updates from the Ubuntu
    28	## security team.
    29	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
    30	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
    31	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
    32	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
    33	
    34	## N.B. software from this repository may not have been tested as
    35	## extensively as that contained in the main release, although it includes
    36	## newer versions of some applications which may provide useful features.
    37	## Also, please note that software in backports WILL NOT receive any review
    38	## or updates from the Ubuntu security team.
    39	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
    40	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
    41	
    42	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
    43	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
    44	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
    45	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
    46	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
    47	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
    48	
    49	## Uncomment the following two lines to add software from Canonical's
    50	## 'partner' repository.
    51	## This software is not part of Ubuntu, but is offered by Canonical and the
    52	## respective vendors as a service to Ubuntu users.
    53	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    54	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    55	
    56	## This software is not part of Ubuntu, but is offered by third-party
    57	## developers who want to ship their latest software.
    58	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
    59	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
    60	# deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # disabled on upgrade to raring
    61	# deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free # disabled on upgrade to raring
    62	# deb [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux
    63	# deb-src [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux
    64	# deb [http://ppa.launchpad.net/nebc/bio-linux/ubuntu](http://ppa.launchpad.net/nebc/bio-linux/ubuntu) precise main # disabled on upgrade to raring
    65	# deb-src [http://ppa.launchpad.net/nebc/bio-linux/ubuntu](http://ppa.launchpad.net/nebc/bio-linux/ubuntu) precise main # disabled on upgrade to raring
    66	deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) raring-getdeb games" >> /etc/apt/sources.list.d/getdeb.list
    67	# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) raring-getdeb games" >> /etc/apt/sources.list.d/getdeb.list
```


Pabibe, thats the output. 

ClaraCC, yours is below.

```

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/


# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
# deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # disabled on upgrade to raring
# deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free # disabled on upgrade to raring
# deb [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux
# deb-src [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux
# deb [http://ppa.launchpad.net/nebc/bio-linux/ubuntu](http://ppa.launchpad.net/nebc/bio-linux/ubuntu) precise main # disabled on upgrade to raring
# deb-src [http://ppa.launchpad.net/nebc/bio-linux/ubuntu](http://ppa.launchpad.net/nebc/bio-linux/ubuntu) precise main # disabled on upgrade to raring
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) raring-getdeb games" >> /etc/apt/sources.list.d/getdeb.list
# deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) raring-getdeb games" >> /etc/apt/sources.list.d/getdeb.list
```

---

### Post by papibe on 2013-05-22
There it is:
```
66	deb http://archive.getdeb.net/ubuntu raring-getdeb games**[COLOR="#FF0000"]" >> /etc/apt/sources.list.d/getdeb.list[/COLOR]**
67	# deb-src http://archive.getdeb.net/ubuntu raring-getdeb games**[COLOR="#FF0000"]" >> /etc/apt/sources.list.d/getdeb.list[/COLOR]**
```
Open an editor as root:
```
gksudo gedit /etc/apt/sources.list
```
Then look for the 2 lines above (no line number), and edit them so they look like this:
```
deb http://archive.getdeb.net/ubuntu raring-getdeb games
# deb-src http://archive.getdeb.net/ubuntu raring-getdeb games
```
Save the file, and update your sources:
```
sudo apt-get update
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by claracc on 2013-05-22
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) this address is not found in the server, it gives 404 error, so you have to remove this ppa from your sources.list file. About the malformed line is: 

deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) raring-getdeb games" [COLOR="#FFA07A"]>> /etc/apt/sources.list.d/getdeb.list[/COLOR] 

if you remove it enterely I think your problems will be finished.

---

### Post by bottaw on 2013-05-22
It worked perfectly!!!! Thank you so much!!!!

---

### Post by claracc on 2013-05-22
> **bottaw said:**
> It worked perfectly!!!! Thank you so much!!!!

Please, mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

