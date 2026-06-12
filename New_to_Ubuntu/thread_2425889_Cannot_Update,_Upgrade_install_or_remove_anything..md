---
title: "Cannot Update, Upgrade install or remove anything. Broken Ubuntu 19.04. Help needed."
date: 2019-09-01
forum: New to Ubuntu
---

### Post by scrypt on 2019-09-01
Ive made a complete mess of my ubuntu 19.04 installation.
Could someone help me to fix it please, preferably from the desktop using the terminal or anything else possible. I Cannot Update, Upgrade, install or remove anything. 

I think it has something to do primarily with this error i get when trying to update ubuntu, or install or remove any kind of package. When I do try update, install etc i get this error which is one of many, but this is the error that appears the most. :

Error while installing package: trying to overwrite '/usr/share/qtermwidget5/translations/qtermwidget_ca.qm', which is also in package qtermwidget-l10n 0.14.1-0ubuntu2.

When I try : sudo apt-get --fix-broken install

I get this error :

```
Preparing to unpack .../qtermwidget5-data_0.14.1-1_all.deb ...
Unpacking qtermwidget5-data (0.14.1-1) over (0.14.1-0ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/qtermwidget5-data_0.14.1-1_all.deb (--unpack):
 trying to overwrite '/usr/share/qtermwidget5/translations/qtermwidget_ca.qm', which is also in package qtermwidget-l10n 0.14.1-0ubuntu2
Errors were encountered while processing:
 /var/cache/apt/archives/qtermwidget5-data_0.14.1-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

When I try : sudo dpkg --configure -a

I get This error :

```
root@tux-OptiPlex-7010:/home/tux# sudo dpkg --configure -a
1567349077 PERROR torsocks[7866]: socks5 libc connect: Connection refused (in socks5_connect() at socks5.c:202)
1567349077 PERROR torsocks[7866]: socks5 libc connect: Connection refused (in socks5_connect() at socks5.c:202)
sudo: unable to resolve host tux-OptiPlex-7010: Non-recoverable failure in name resolution
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
1567349077 WARNING torsocks[7866]: [syscall] Unsupported syscall number 39. Denying the call (in tsocks_syscall() at syscall.c:605)
dpkg: dependency problems prevent configuration of libqtermwidget5-0:amd64:
 libqtermwidget5-0:amd64 depends on qtermwidget5-data (= 0.14.1-1); however:
  Version of qtermwidget5-data on system is 0.14.1-0ubuntu2
```

```
dpkg: error processing package libqtermwidget5-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qterminal:
 qterminal depends on libqtermwidget5-0 (>= 0.14.1~); however:
  Package libqtermwidget5-0:amd64 is not configured yet
```

```
dpkg: error processing package qterminal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqtermwidget5-0:amd64
 qterminal.
```

Nothing i have tried has managed to fix this.
Can someone kindly help me to fix this mess, so i can learn from it and hopefully not let it happen again. I hope someone can help.

Thanks in advance.

---

### Post by oldfred on 2019-09-01
Are you running as root?
> root@tux-OptiPlex-7010:/home/tux#

       Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[http://xkcd.com/149/](http://xkcd.com/149/) 
    
Are you using a ppa?
I might comment that out, to see if that fixes it.

       # List sources, if you post here, be sure to use code tags, # in Forum's advanced editor.
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

---

### Post by scrypt on 2019-09-01
i was running as root by running : sudo su, for convenience.
and im not sure if im using ppa or not. How exactly would i check for this ?
and what should i be using if not ppa ?
How would i comment that out correctly? I cant open software and updates, it wont open.
could you kindly elaborate please.

when i ran : sudo apt update

I got this output :

```
tux@tux-OptiPlex-7010:~$ sudo apt update
[sudo] password for tux: 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:2 [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) disco InRelease        
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:4 [http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu](http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu) disco InRelease      
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security InRelease [97.5 kB]     
Hit:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) disco InRelease                      
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) disco-updates InRelease [97.5 kB]    
Hit:8 [http://ppa.launchpad.net/lutris-team/lutris/ubuntu](http://ppa.launchpad.net/lutris-team/lutris/ubuntu) disco InRelease       
Hit:9 [https://deb.torproject.org/torproject.org](https://deb.torproject.org/torproject.org) disco InRelease                
Hit:10 [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) disco InRelease  
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) disco-backports InRelease [88.8 kB] 
Hit:13 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) cosmic InRelease                    
Hit:14 [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) disco InRelease
Hit:15 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) disco InRelease        
Hit:17 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) disco InRelease                     
Err:18 [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) disco Release         
  404  Not Found [IP: 91.189.95.83 80]
Hit:16 [http://mirror.serverius.net/kali](http://mirror.serverius.net/kali) kali-rolling InRelease        
Hit:19 [https://packagecloud.io/asbru-cm/asbru-cm/ubuntu](https://packagecloud.io/asbru-cm/asbru-cm/ubuntu) disco InRelease
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

sudo apt full-upgrade

gives me ::

tux@tux-OptiPlex-7010:~$ apt --fix-broken install
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?


Im back using ubuntu after a long break, so ive forgotten alot.

---

### Post by oldfred on 2019-09-01
ERR 18 says your problem.

```
E: The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

You can list your sources as in previous post & then manually edit the ppa by adding # at beginning of line.

If in your sources list:
       # Edit Sources
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list 
    
Or if in /etc/apt/sources.list.d edit file in that folder the same way.

---

### Post by Impavidus on 2019-09-01
oldfred found a problem, not necessarily the only problem. You've got two packages on your system, qtermwidget5-data and qtermwidget-l10n, which cannot be installed at the same time. For packages from the official repos this is usually prevented by dependency rules, but for packages from other sources, this doesn't always work. You have to remove one of those packages before you can install the other. I don't know those packages.

Also, do you know how sudo works? It allows you to run a command as a different user, usually root. If you already are the root user (by running a root shell), there's no need to become the root user. You started that root shell so you didn't have to type sudo so often, right? So no need for sudo, although it won't hurt.

---

### Post by scrypt on 2019-09-02
Thank-you for your replies.

I must admit im still stuck with this issue.
Regarding oldfreds reply :

> **oldfred said:**
> ERR 18 says your problem.

```
E: The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

You can list your sources as in previous post & then manually edit the ppa by adding # at beginning of line.

If in your sources list:
       # Edit Sources
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo nano /etc/apt/sources.list 
    
Or if in /etc/apt/sources.list.d edit file in that folder the same way.

Im not sure what I need to comment out in my sources.list.
Here is my sources.list :

```
sudo nano /etc/apt/sources.list ::

# deb cdrom:[Ubuntu 18.10 _Cosmic Cuttlefish_ - Release amd64 (20181017.3)]/ cosmic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-updates universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-updates multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) cosmic partner
# deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) cosmic partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) cosmic-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security universe
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) cosmic-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) cosmic-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.



# Kali linux repositories | Added by Katoolin
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free
```

I think its this error which needs fixing (please let me know if its not)
when I run sudo dpkg --configure -a. I get this error which i don't know how to fix.
Can someone help me fix this please.

sudo dpkg --configure -a :


ux@tux-OptiPlex-7010:~$ sudo dpkg --configure -a
[sudo] password for tux: 
dpkg: dependency problems prevent configuration of libqtermwidget5-0:amd64:
 libqtermwidget5-0:amd64 depends on qtermwidget5-data (= 0.14.1-1); however:
  Version of qtermwidget5-data on system is 0.14.1-0ubuntu2.

dpkg: error processing package libqtermwidget5-0:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qterminal:
 qterminal depends on libqtermwidget5-0 (>= 0.14.1~); however:
  Package libqtermwidget5-0:amd64 is not configured yet.

dpkg: error processing package qterminal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqtermwidget5-0:amd64
 qterminal

Could someone kindly clarify what I need to do to fix this problem please ?

---

### Post by oldfred on 2019-09-02
You did not run this, which would also show show all the folders in /etc/apt/sources.list.d which we need to see. You do not need to post the first part as you already have posted sources. But use code tags, please.

# List sources, if you post here, be sure to use code tags, # in Forum's advanced editor.
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;                 


You also show at least one cosmic & mostly disco sources. And one from kali. 

I would comment these out. Not sure if kali would contribute to issue or not.
       deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) cosmic partner
deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free 
    
But your error in update Err 18 must be in sources.d

---

### Post by scrypt on 2019-09-02
ux@tux-OptiPlex-7010:~$ find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

```
/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 18.10 _Cosmic Cuttlefish_ - Release amd64 (20181017.3)]/ cosmic main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco main restricted
     6    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-updates main restricted
    11    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco universe
    17    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic universe
    18    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-updates universe
    19    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco multiverse
    27    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic multiverse
    28    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-updates multiverse
    29    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) disco-backports main restricted universe multiverse
    37    # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) cosmic-backports main restricted universe multiverse
    38    
    39    ## Uncomment the following two lines to add software from Canonical's
    40    ## 'partner' repository.
    41    ## This software is not part of Ubuntu, but is offered by Canonical and the
    42    ## respective vendors as a service to Ubuntu users.
    43    deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) cosmic partner
    44    # deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) cosmic partner
    45    
    46    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security main restricted
    47    # deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) cosmic-security main restricted
    48    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security universe
    49    # deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) cosmic-security universe
    50    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) disco-security multiverse
    51    # deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) cosmic-security multiverse
    52    
    53    # This system was installed using small removable media
    54    # (e.g. netinst, live or single CD). The matching "deb cdrom"
    55    # entries were disabled at the end of the installation process.
    56    # For information about how to configure apt package sources,
    57    # see the sources.list(5) manual.
    58    
    59    
    60    
    61    # Kali linux repositories | Added by Katoolin
    62    deb [http://http.kali.org/kali](http://http.kali.org/kali) kali-rolling main contrib non-free

/etc/apt/sources.list.d/asbru-cm_asbru-cm.list

     1    # this file was generated by packagecloud.io for
     2    # the repository at [https://packagecloud.io/asbru-cm/asbru-cm](https://packagecloud.io/asbru-cm/asbru-cm)
     3    
     4    deb [https://packagecloud.io/asbru-cm/asbru-cm/ubuntu/](https://packagecloud.io/asbru-cm/asbru-cm/ubuntu/) disco main
     5    deb-src [https://packagecloud.io/asbru-cm/asbru-cm/ubuntu/](https://packagecloud.io/asbru-cm/asbru-cm/ubuntu/) disco main

/etc/apt/sources.list.d/i2p-maintainers-ubuntu-i2p-disco.list

     1    deb [http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu/](http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu/) disco main
     2    # deb-src [http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu/](http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu/) disco main
     3    
     4    
     5    

/etc/apt/sources.list.d/google-chrome.list

     1    ###
     2    ###
     3    ###
     4    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     5    # You may comment out this entry, but any other modifications may be lost.
     6    # deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
     7    
     8    
     9    

/etc/apt/sources.list.d/gnome-shell-extensions-ubuntu-ppa-disco.list


/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-disco.list

     1    # deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) disco main
     2    # deb-src [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) disco main
     3    
     4    
     5    

/etc/apt/sources.list.d/plushuang-tw-ubuntu-uget-stable-disco.list

     1    deb [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) disco main
     2    # deb-src [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) disco main
     3    # deb-src [http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu](http://ppa.launchpad.net/plushuang-tw/uget-stable/ubuntu) disco main

/etc/apt/sources.list.d/tor.list

     1    deb [https://deb.torproject.org/torproject.org/](https://deb.torproject.org/torproject.org/) disco main
     2    
     3    
     4    

/etc/apt/sources.list.d/webupd8team-ubuntu-java-disco.list

     1    deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) disco main
     2    # deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) disco main

/etc/apt/sources.list.d/lutris-team-ubuntu-lutris-disco.list

     1    deb [http://ppa.launchpad.net/lutris-team/lutris/ubuntu](http://ppa.launchpad.net/lutris-team/lutris/ubuntu) disco main
     2    # deb-src [http://ppa.launchpad.net/lutris-team/lutris/ubuntu](http://ppa.launchpad.net/lutris-team/lutris/ubuntu) disco main

/etc/apt/sources.list.d/google-chrome-beta.list

     1    ###
     2    ###
     3    ###
     4    ### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     5    # You may comment out this entry, but any other modifications may be lost.
     6    deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
     7    
     8    
     9    

/etc/apt/sources.list.d/disco-partner.list

     1    # channel for the disco (19.04) partner channel
     2    
     3    #:description:This channel contains the partner software for disco
     4    deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) disco partner
     5    
     6    
     7    

/etc/apt/sources.list.d/diesch-ubuntu-testing-disco.list

     1    # deb [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) disco main
     2    # deb-src [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) disco main

/etc/apt/sources.list.d/clipgrab-team-ubuntu-ppa-disco.list

     1    deb [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) disco main
     2    # deb-src [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) disco main

/etc/apt/sources.list.d/oibaf-ubuntu-graphics-drivers-disco.list

     1    deb [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/) disco main
     2    # deb-src [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/) disco main
     3    # deb-src [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/) disco main
     4    # deb-src [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/) disco main
     5    # deb-src [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/) disco main
     6    
     7    
     8    
```

I will read up on :
# List sources, if you post here, be sure to use code tags, # in Forum's advanced editor. I dont know how to edit uncomment the above.
im not sure what this means yet.

---

### Post by oldfred on 2019-09-02
You can easily add code tags using Forum's advanced editor and # icon. 

       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)
If using Quick Reply then  at the beginning and  at the end use these: 
( [noparse]```
 and 
```[/noparse] ) 

Awful lot of ppas. 
find this one and comment it out.

[http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) disco Release

---

### Post by scrypt on 2019-09-03
Apologies but I don't know how to do this :
im unsure what i need to do here to fix this?
how do i find and edit sources.d

---

### Post by scrypt on 2019-09-03
okay.. so, i appreciate the replies but im still unsure how and what i need to do to fix my original problem, could someone kindly tell me how to fix this please ??

---

### Post by scrypt on 2019-09-03
> **oldfred said:**
> You can easily add code tags using Forum's advanced editor and # icon. 

       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)
[http://www.bbcode.org/reference.php](http://www.bbcode.org/reference.php)
If using Quick Reply then  at the beginning and  at the end use these: 
( [noparse]```
 and 
```[/noparse] ) 
[http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) disco Release

Thank-you very much for your help.
the above worked as far as i commented out : 
but, i cant find :
http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu[/URL] disco Release[
Although I'm having difficulty opening and editing /etc/apt/sources.list.d.
When i use :
sudo nano /etc/apt/sources.list.d
Opens an empty terminal window stating that /etc/apt/sources.list.d
Is a directory. So, how do i edit that ?

Im also still a little unsure howto edit the output when i ran your earlier command :

find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
 
I can see alot more ppa's id like to remove in the given output when i run the above command
How do i open and edit the 
find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
output ?
Also when i run sudo apt update i get this error :

```
E: The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu disco Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

As i mentioned i cant seem to find The repository 'http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu disco Release.
Can you tell me how to find and remove that please ?

---

### Post by oldfred on 2019-09-03
Now each ppa you add, creates a new folder/file under /etc/apt/sources.list.d.

ls -l /etc/apt/sources.list.d

You also posted it in your post #8
```
        /etc/apt/sources.list.d/clipgrab-team-ubuntu-ppa-disco.list 
   
  1    deb [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) disco main
 2    # deb-src [http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) disco main 
     
```

But you have many (too many?) ppa installed.
Generally when you upgrade you remove all ppas and all proprietary drivers as new version may not need then or they are not available for the new version.

---

### Post by dapidc-brambang on 2019-11-28
You can edit 
/etc/apt/sources.list.d/clipgrab-team-ubuntu-ppa-disco.list

comment the first line then save.

---

