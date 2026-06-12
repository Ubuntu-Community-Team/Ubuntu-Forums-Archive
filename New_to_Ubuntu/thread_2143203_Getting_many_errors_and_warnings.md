---
title: "Getting many errors and warnings"
date: 2013-05-08
forum: New to Ubuntu
---

### Post by Keshav2050 on 2013-05-08
I tried to add unity lens calculator and some other things in ubuntu 13.04, but I ended up getting many errors. when I run 'sudo apt-get update' I get

```
Err http://glug.nith.ac.in raring/main Sources  404  Not Found
Err http://glug.nith.ac.in raring/restricted Sources
  404  Not Found
Err http://glug.nith.ac.in raring/universe Sources
  404  Not Found
Err http://glug.nith.ac.in raring/multiverse Sources
  404  Not Found
Err http://glug.nith.ac.in raring/main i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring/restricted i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring/universe i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring/multiverse i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-updates/main Sources
  404  Not Found
Err http://glug.nith.ac.in raring-updates/restricted Sources
  404  Not Found
Err http://glug.nith.ac.in raring-updates/universe Sources
  404  Not Found
Err http://glug.nith.ac.in raring-updates/multiverse Sources
  404  Not Found
Err http://glug.nith.ac.in raring-updates/main i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-updates/restricted i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-updates/universe i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-updates/multiverse i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-backports/main Sources
  404  Not Found
Err http://glug.nith.ac.in raring-backports/restricted Sources
  404  Not Found
Err http://glug.nith.ac.in raring-backports/universe Sources
  404  Not Found
Err http://glug.nith.ac.in raring-backports/multiverse Sources
  404  Not Found
Err http://glug.nith.ac.in raring-backports/main i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-backports/restricted i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-backports/universe i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-backports/multiverse i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-security/main Sources
  404  Not Found
Err http://glug.nith.ac.in raring-security/restricted Sources
  404  Not Found
Err http://glug.nith.ac.in raring-security/universe Sources
  404  Not Found
Err http://glug.nith.ac.in raring-security/multiverse Sources
  404  Not Found
Err http://glug.nith.ac.in raring-security/main i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-security/restricted i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-security/universe i386 Packages
  404  Not Found
Err http://glug.nith.ac.in raring-security/multiverse i386 Packages
  404  Not Found
W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring/main/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring/restricted/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring/universe/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring/multiverse/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-updates/main/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-updates/restricted/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-updates/universe/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-updates/multiverse/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-updates/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-updates/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-updates/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-updates/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-backports/main/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-backports/restricted/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-backports/universe/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-backports/multiverse/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-backports/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-backports/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-backports/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-backports/multiverse/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-security/main/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-security/restricted/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-security/universe/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-security/multiverse/source/Sources  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-security/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-security/restricted/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-security/universe/binary-i386/Packages  404  Not Found


W: Failed to fetch http://glug.nith.ac.in/ubuntu/archives/dists/raring-security/multiverse/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by fantab on 2013-05-08
check you internet connectivity.

You will check your sources.list and remove the errant repository.

gksudo gedit /etc/apt/sources.list

Edit: I just checkd, I think some of the "GLUG" webpages are not working or may be temporarily down. Try changing to another server from 'Software Center'.

---

### Post by Keshav2050 on 2013-05-08
When I tried to run '[COLOR=#000000]gksudo gedit /etc/apt/sources.list' I got
```
[/COLOR]The program 'gksudo' is currently not installed. You can install it by typing:[COLOR=#000000]
[/COLOR]
sudo apt-get install gksu[COLOR=#000000]
```

when I tried to install by '[/COLOR]sudo apt-get install gksu[COLOR=#000000]' I got
```
[/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
 unity-lens-answers : Depends: python-simplejson but it is not going to be installed

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[COLOR=#000000]
```

When I typed '[/COLOR]sudo apt-get -f install gksu[COLOR=#000000]'
```
[/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
 unity-lens-answers : Depends: python-simplejson but it is not going to be installed

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[COLOR=#000000]
```
again. So I just typed sudo then I got
```
[/COLOR](gedit:3734): IBUS-WARNING **: The owner of /home/keshav/.config/ibus/bus is not root!

[COLOR=#000000]
```

and in sources.list
```
[/COLOR]# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://glug.nith.ac.in/ubuntu/archives/ raring main restricted
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://glug.nith.ac.in/ubuntu/archives/ raring-updates main restricted
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://glug.nith.ac.in/ubuntu/archives/ raring universe
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring universe
deb http://glug.nith.ac.in/ubuntu/archives/ raring-updates universe
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://glug.nith.ac.in/ubuntu/archives/ raring multiverse
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring multiverse
deb http://glug.nith.ac.in/ubuntu/archives/ raring-updates multiverse
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://glug.nith.ac.in/ubuntu/archives/ raring-backports main restricted universe multiverse
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring-backports main restricted universe multiverse


deb http://glug.nith.ac.in/ubuntu/archives/ raring-security main restricted
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring-security main restricted
deb http://glug.nith.ac.in/ubuntu/archives/ raring-security universe
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring-security universe
deb http://glug.nith.ac.in/ubuntu/archives/ raring-security multiverse
deb-src http://glug.nith.ac.in/ubuntu/archives/ raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main
deb http://archive.canonical.com/ raring partner

# deb-src http://archive.canonical.com/ raring partner[COLOR=#000000]
```

What should I do now, remove all the glug web pages or something else?[/COLOR]

---

### Post by fantab on 2013-05-08
"apt-get -f install" corrects/fixes broken packages, and its a command by itself, you don't add anything after "install".

Yes. Comment out GLUG repos and run '*sudo apt-get update*'.

To 'comment out' you have to add "#" at the beginning of the line, like:

[COLOR=#ff0000]**#**[/COLOR]deb [http://glug.nith.ac.in/ubuntu/archives/](http://glug.nith.ac.in/ubuntu/archives/) raring main restricted [COLOR=#ff0000][B]
#[/B][/COLOR]deb-src [http://glug.nith.ac.in/ubuntu/archives/](http://glug.nith.ac.in/ubuntu/archives/) raring main restricted

Also you can edit /etc/apt/sources only as root, if you can't gksudo then:
```
sudo -i
gedit /etc/apt/sources.list
```
And don't forget to SAVE the file.

If you still see any errors, then post the output of 'apt-get update'.

---

### Post by Keshav2050 on 2013-05-08
Thank you very much, that solved the problem. Can you please tell me how to install gksu, and since I commented those sources will I not need them?

---

### Post by fantab on 2013-05-08
> **Keshav2050 said:**
> Thank you very much, that solved the problem. Can you please tell me how to install gksu, and since I commented those sources will I not need them?

If you have not put those sources there, then I must ask you, "from where did you get your Ubuntu install copy"? Those repos are not part of 'Official' Ubuntu release. 

"gksu" is not needed. you can use "sudo -i" instead. gksu/gksudo is used to open GUI applications as 'root'. Apparently, according to Ubuntu developer's ([http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-13-04](http://askubuntu.com/questions/284306/why-is-gksu-no-longer-installed-by-default-in-13-04)) it is not needed anymore.

Note after using "sudo -i" you should use "exit" to exit sudo.

---

### Post by Keshav2050 on 2013-05-08
Thanks, I actually don't remember but this problem occurred only after trying to install different unity-lens like weather, calculator, etc which are not working in Ubuntu 13.04.

---

