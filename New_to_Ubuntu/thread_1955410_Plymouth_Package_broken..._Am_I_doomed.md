---
title: "Plymouth Package broken... Am I doomed?"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by JulienEP6 on 2012-04-09
Hi everybody!

I have a broken package... So far nothing horrible. 

The problem is that it is Plymouth, and it seems that if I remove it, I will remove half of the packages of my system... So here is my question: if I actually remove, or even purge **plymouth**; will I at least have a terminal left after it to reinstall it? Or am I definitely doomed?

Just to illustrate what I say; here is the result of an[/FONT]

> apt-get --reinstall install plymouth:

    ```
julien@julien-desktop:~$ sudo apt-get --reinstall install plymouth
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Reinstallation of plymouth is not possible, it cannot be downloaded.
    You might want to run 'apt-get -f install' to correct these:
    The following packages have unmet dependencies:
     plymouth : Depends: libdrm-nouveau1 (>= 2.4.11-1ubuntu1~) but it is not installable
                Recommends: plymouth-themes-all but it is not installable
    E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

or an
> apt-get -f install
 
(well basically it is the same)

   ```
 julien@julien-desktop:~$ sudo apt-get -f install
    [sudo] password for julien: 
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Correcting dependencies... failed.
    The following packages have unmet dependencies:
     plymouth : Depends: libdrm-nouveau1 (>= 2.4.11-1ubuntu1~) but it is not installable
                Recommends: plymouth-themes-all but it is not installable
    E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
    E: Unable to correct dependencies
    julien@julien-desktop:~$ 
```

Any idea would be very welcome...

PS: I'm sorry I already post this on an other forum (namely: ask ubuntu), but I really need a solution.

PPS: if someone want to know how that possibly happened... Well, I more or less have the problem since installation (yesterday): system didn't want to perform full update (see [http://askubuntu.com/questions/80895/partial-upgrade-error/120390#120390](http://askubuntu.com/questions/80895/partial-upgrade-error/120390#120390)). After one day I decided to take care of the pb: python was one of the reluctant packages, said it had conflicts with an other package. I tried to force overwrite when upgrading plymouth... didn't quite work...)

---

### Post by NikTh on 2012-04-09
Hello JulienEP6 , 
Try these ```
sudo apt-get autoremove
sudo apt-get autoclean 
sudo rm -rf /var/lib/apt/lists/* 
sudo apt-get update 
sudo apt-get dist-upgrade
```If above commands don't solve your problem , then go to a console (Ctrl+Atl+F2) login and give this command 
```
sudo dpkg-reconfigure xserver-xorg
``` or ```
sudo dpkg-reconfigure x11-common
``` If the above command don't solve the problem , then reboot and go to "recovery mode" and try "Dpkg Repair Broken Packages" 

Thanks

---

### Post by JulienEP6 on 2012-04-10
Thanks for answer! Finally got an other answer which worked before I could try yours: I updated mountall to a version without dependences on plymouth, then removing plymouth was not a problem anymore. Here is what I was proposed to do and which actually worked:

[INDENT][I]It is possible to remove it. The [bug report #556372]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/556372http://") describes the problem. Dave Lentz has a PPA which works around those issues. So you have to add the PPA:

```
sudo apt-add-repository ppa:dtl131/mediahacks
sudo aptitude update
```

Now you have to update mountall to version (as of April 2012): 2.25ubuntu2~mediahacks1. When this is finished you can deinstall plymouth without deinstalling half of your system.[/I][/INDENT]


Actually for oniric the correct version of mountall was 2.31ubuntu1~mediahacks1, but it depends of the distribution you use... Well... actually as I haven't restarted since then, I don't know what I have instead of the plymouth-generated screen now... Probably simply the commands executed.


Nevertheless I will probably use your imput, as I have 2 other dirty packages (namely **python-cairo** and **python-notify**). I wonder if something was wrong with my install from the begining or if I have/had too much sources in my list... The problem is that when I clean the list, it gets dirty and full of stuff again each time I start *[I]Ubuntu Software Center*[/I]...

For example I'm wondering why it always put both:
```

deb http://archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
```

and then the same ones with the "de" before?:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
```

Does it make sense?

---

### Post by anewguy on 2012-04-10
What country are you in?  

Dave ;)

---

### Post by JulienEP6 on 2012-04-10
Ahah, the country is the right one (it's germany), I was just wondering why there is one with the country and one without the country. And the difference between them.

Naja... I guess it does not hurt anyway... just seemed strange to me.

---

### Post by JulienEP6 on 2012-04-10
By the way thanks again NikTh! The big cleaning you proposed did the job for my **python** packages! Hurrah! I have a clean ubuntu again!

---

### Post by NikTh on 2012-04-10
Glad you fixed it. :D 

You can mark Thread as solved if you want (Thread tools).

---

### Post by NikTh on 2012-04-10
.....

---

