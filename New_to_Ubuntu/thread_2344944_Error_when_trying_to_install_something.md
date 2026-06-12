---
title: "Error when trying to install something"
date: 2016-11-29
forum: New to Ubuntu
---

### Post by dolm2 on 2016-11-29
Hello,

an hour ago i tried to install Spotify on Kubuntu 16.04 (I know it's not supported, but it is something I really miss). I have to mention that I'm completely new to Ubuntu, programmed some C(++) on it for like 2 weeks now.
But now I get this error when trying to install something :

[FONT=monospace][COLOR=#000000]E: Malformed line 5 in source list /etc/apt/sources.list.d/spotify.list (type)[/COLOR]
E: The list of sources could not be read.
E: Malformed line 5 in source list /etc/apt/sources.list.d/spotify.list (type)
E: The list of sources could not be read.
[/FONT]
I think it happened after I used this command: sudo tee /etc/apt/sources.list.d/spotify.list

I don't know how to fix this, can't even update list of available packages...
Can anyone help?

---

### Post by howefield on 2016-11-29
Just for information there is the web player at [https://play.spotify.com/](https://play.spotify.com/) which can be accessed with any web browser.

Can you give the output of..

```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d/
```

---

### Post by dolm2 on 2016-11-29
My sources.list:

```
# deb cdrom:[Kubuntu 16.10 _Yakkety Yak_ - Release amd64 (20161012.1)]/ yakkety main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ yakkety main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ yakkety main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ yakkety-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ yakkety universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ yakkety universe
deb http://de.archive.ubuntu.com/ubuntu/ yakkety-updates universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ yakkety-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ yakkety multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ yakkety multiverse
deb http://de.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ yakkety-updates multiverse

## N.B. software from this repository may not have been tested as                                                                                                                                
## extensively as that contained in the main release, although it includes                                                                                                                       
## newer versions of some applications which may provide useful features.                                                                                                                        
## Also, please note that software in backports WILL NOT receive any review                                                                                                                      
## or updates from the Ubuntu security team.                                                                                                                                                     
deb http://de.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse                                                                                                   
# deb-src http://de.archive.ubuntu.com/ubuntu/ yakkety-backports main restricted universe multiverse                                                                                             
                                                                                                                                                                                                 
## Uncomment the following two lines to add software from Canonical's                                                                                                                            
## 'partner' repository.                                                                                                                                                                         
## This software is not part of Ubuntu, but is offered by Canonical and the                                                                                                                      
## respective vendors as a service to Ubuntu users.                                                                                                                                              
# deb http://archive.canonical.com/ubuntu yakkety partner                                                                                                                                        
# deb-src http://archive.canonical.com/ubuntu yakkety partner

deb http://security.ubuntu.com/ubuntu yakkety-security main restricted
# deb-src http://security.ubuntu.com/ubuntu yakkety-security main restricted
deb http://security.ubuntu.com/ubuntu yakkety-security universe
# deb-src http://security.ubuntu.com/ubuntu yakkety-security universe
deb http://security.ubuntu.com/ubuntu yakkety-security multiverse
# deb-src http://security.ubuntu.com/ubuntu yakkety-security multiverse




```

sources.list.d directory:


```
mehanik-ubuntu-ksuperkey-yakkety.list  mehanik-ubuntu-ksuperkey-yakkety.list.save  spotify.list


```

---

### Post by howefield on 2016-11-29
OK, do..

```
sudo rm /etc/apt/sources.list.d/spotify.list
```

The instructions for adding spotify are here : [https://www.spotify.com/uk/download/linux/](https://www.spotify.com/uk/download/linux/)

---

