---
title: "Pending updates... but there are no updates :o"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-08
This darn little red ! won't go away...

[http://s27.postimg.org/uqzcj1qwj/Screenshot_from_2014_05_08_18_10_52.png](http://s27.postimg.org/uqzcj1qwj/Screenshot_from_2014_05_08_18_10_52.png)

It says to click "show updates" to check and the alert should drop but there are no updates and the alert remains.

Reboot had no effect.

Any ideas ghuyz?

---

### Post by papibe on 2014-05-08
Hi Drowz0r.

Could you open a terminal run these commands, and post back the results (you can copy/paste the text)?
```
sudo apt-get update

sudo apt-get -s upgrade
```
Regards.

---

### Post by sandyd on 2014-05-08
Can you post the output of
```

sudo apt-get update
sudo apt-get upgrade

```

Thanks.

---

### Post by Drowz0r on 2014-05-08
Yellow, thanks for the replies, I guess it's just the bottom bit with the fails you want?
```

Fetched 27.1 MB in 14s (1,893 kB/s)                                            
W: Failed to fetch http://deb.playonlinux.com/dists/trusty/main/binary-amd64/Packages  404  Not Found [IP: 37.187.89.171 80]

W: Failed to fetch http://deb.playonlinux.com/dists/trusty/main/binary-i386/Packages  404  Not Found [IP: 37.187.89.171 80]

W: Failed to fetch http://repo.steampowered.com/steam/dists/trusty/steam/source/Sources  404  Not Found [IP: 90.223.216.161 80]

W: Failed to fetch http://repo.steampowered.com/steam/dists/trusty/steam/binary-amd64/Packages  404  Not Found [IP: 90.223.216.161 80]

W: Failed to fetch http://repo.steampowered.com/steam/dists/trusty/steam/binary-i386/Packages  404  Not Found [IP: 90.223.216.161 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Not sure which part of the next bit you wanted, so here is everything:

```
drowz0r@Prime:~$ sudo apt-get -s upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins-default cups-browsed
  cups-filters cups-filters-core-drivers gir1.2-freedesktop gir1.2-glib-2.0
  gir1.2-nautilus-3.0 libcompizconfig0 libcupsfilters-dev libcupsfilters1
  libcupsfilters1:i386 libdecoration0 libfontembed1 libgirepository-1.0-1
  libnautilus-extension1a nautilus nautilus-data unity-greeter
21 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Inst libcupsfilters-dev [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libcupsfilters1 [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64]) [libcupsfilters1:amd64 on libcupsfilters1:i386] [libcupsfilters1:i386 on libcupsfilters1:amd64] [libcupsfilters1:i386 ]
Inst libcupsfilters1:i386 [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Inst libfontembed1 [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-freedesktop [1.40.0-1] (1.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libgirepository-1.0-1 [1.40.0-1] (1.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst gir1.2-glib-2.0 [1.40.0-1] (1.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libcompizconfig0 [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst compiz-gnome [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst compiz-plugins-default [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst libdecoration0 [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64]) []
Inst compiz-core [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Inst compiz [1:0.9.11+14.04.20140409-0ubuntu1] (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Inst cups-browsed [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst cups-filters-core-drivers [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst cups-filters [1.0.52-0ubuntu1] (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libnautilus-extension1a [1:3.10.1-0ubuntu8] (1:3.10.1-0ubuntu9 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-nautilus-3.0 [1:3.10.1-0ubuntu8] (1:3.10.1-0ubuntu9 Ubuntu:14.04/trusty-updates [amd64])
Inst nautilus-data [1:3.10.1-0ubuntu8] (1:3.10.1-0ubuntu9 Ubuntu:14.04/trusty-updates [all])
Inst nautilus [1:3.10.1-0ubuntu8] (1:3.10.1-0ubuntu9 Ubuntu:14.04/trusty-updates [amd64])
Inst unity-greeter [14.04.9-0ubuntu1] (14.04.10-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libcupsfilters1 (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libcupsfilters1:i386 (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [i386])
Conf libcupsfilters-dev (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libfontembed1 (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libgirepository-1.0-1 (1.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-glib-2.0 (1.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-freedesktop (1.40.0-1ubuntu0.1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz-core (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libcompizconfig0 (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf libdecoration0 (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz-plugins-default (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz-gnome (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf compiz (1:0.9.11+14.04.20140423-0ubuntu1 Ubuntu:14.04/trusty-updates [all])
Conf cups-browsed (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-filters-core-drivers (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf cups-filters (1.0.52-0ubuntu1.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libnautilus-extension1a (1:3.10.1-0ubuntu9 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-nautilus-3.0 (1:3.10.1-0ubuntu9 Ubuntu:14.04/trusty-updates [amd64])
Conf nautilus-data (1:3.10.1-0ubuntu9 Ubuntu:14.04/trusty-updates [all])
Conf nautilus (1:3.10.1-0ubuntu9 Ubuntu:14.04/trusty-updates [amd64])
Conf unity-greeter (14.04.10-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
drowz0r@Prime:~$ 
```

I've recently gone from 12.04 LTS to 14.04 LTS, around a week or so ago but this ! thing has only started happening in the last two days.

I'm no expert but I guess it's something to do with my software sources? Those sources seem to be necessary to my other applications though...

---

### Post by sandyd on 2014-05-08
Looks like some repos dont have trusty yet.
Can you post the output of
```

cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by Drowz0r on 2014-05-08
Sure

```
drowz0r@Prime:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

and

```
drowz0r@Prime:~$ ls /etc/apt/sources.list.d
costales-folder-color-trusty.list
costales-folder-color-trusty.list.save
dropbox.list.distUpgrade
dropbox.list.save
pipelight-stable-trusty.list
pipelight-stable-trusty.list.save
playonlinux.list
playonlinux.list.distUpgrade
playonlinux.list.save
skype-wrapper-ppa-precise.list
skype-wrapper-ppa-precise.list.distUpgrade
skype-wrapper-ppa-precise.list.save
steam.list
steam.list.distUpgrade
steam.list.save
ticket-to-ride.list
ticket-to-ride.list.distUpgrade
ticket-to-ride.list.save
webupd8team-java-precise.list
webupd8team-java-precise.list.distUpgrade
webupd8team-java-precise.list.save
drowz0r@Prime:~$ 

```

Is trusty a new thing? I think it's a new thing...

They worked fine on 12.04 LTS so I'm guessing it's a... new thing.

---

### Post by papibe on 2014-05-08
It looks like some of ppa's you added (playonlinux and steam), do not have yet the sources and packages for trusty.

Let's see those ppa's details. Could you run this command and post back its results:
```
find /etc/apt/sources.list.d/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by Drowz0r on 2014-05-08
Here we go:
```

drowz0r@Prime:~$ find /etc/apt/sources.list.d/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/pipelight-stable-trusty.list

     1    deb http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main
     2    deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main

/etc/apt/sources.list.d/playonlinux.list

     1    deb http://deb.playonlinux.com/ trusty main # disabled on upgrade to trusty

/etc/apt/sources.list.d/steam.list

     1    deb [arch=amd64,i386] http://repo.steampowered.com/steam/ trusty steam # disabled on upgrade to trusty
     2    deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ trusty steam # disabled on upgrade to trusty

/etc/apt/sources.list.d/webupd8team-java-precise.list

     1    deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main # disabled on upgrade to trusty
     2    deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main # disabled on upgrade to trusty

/etc/apt/sources.list.d/costales-folder-color-trusty.list

     1    deb http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main
     2    deb-src http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main

/etc/apt/sources.list.d/ticket-to-ride.list

     1    # Days of Wonder, Ticket to Ride
     2    # deb http://downloads.daysofwonder.com/ticket-to-ride/repositories/apt stable main # disabled on upgrade to trusty

/etc/apt/sources.list.d/skype-wrapper-ppa-precise.list

     1    deb http://ppa.launchpad.net/skype-wrapper/ppa/ubuntu trusty main # disabled on upgrade to trusty
     2    deb-src http://ppa.launchpad.net/skype-wrapper/ppa/ubuntu trusty main # disabled on upgrade to trusty
drowz0r@Prime:~$ 

```

---

### Post by papibe on 2014-05-08
Thanks. Confirmed: Playonlinux does not have trusty sources and packages yet.

As for steam, my guess is maybe the ppa is not necessary anymore, but I'm not sure. As right now, there's no trusty repositories on that particular steam ppa.

I'd recommend for now disabling, or removing both ppas. You can easily do it on the 'Software Sources' (read [here]("http://askubuntu.com/questions/65911/how-can-i-fix-a-404-error-when-updating-packages")).

Once that is taking cared of, run again 'sudo apt-get update'. If it is clean, you shoud be able to go to the graphical updater, click check and uprade the pending pacakges.

Let us know it goes.
Regards.

---

### Post by Drowz0r on 2014-05-08
Disabled the two steam and one PoL ppa.
Ran suto apt-get update
Did the little "show updates" on the graphical red ! icon thing, no updates

About 10 seconds later it disappeared, so I think that has done it. Hurray~

I don't suppose there will be any way of knowing that I should turn them back on at some point?

---

