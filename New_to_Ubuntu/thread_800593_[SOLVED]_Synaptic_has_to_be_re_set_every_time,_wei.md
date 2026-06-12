---
title: "[SOLVED] Synaptic has to be re set every time, weird?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by tropdoug on 2008-05-20
I just did a reinstall of my ubuntu system on the laptop, cos I messed a few things up. Anyway I am trying to download packages and updates. I have edited the /etc/apt/sources.list to remove all commented out 'deb' lines, and saved it --  all good there. 

When I go into Synaptic and select the server i normally use, I can download maybe 5 or 10 packages and then the rest fail. 

If I try it again, zilch, everything fails. I shut it down and re start and same thing it completely fails. So I select another server, same thing. Its very weird

has anyone got any ideas please?

---

### Post by jtibau on 2008-05-20
This thing happens to me only when I'm behind a webproxy that is filtering content if you don't set it up in your application :(... I'm not sure if that is the right description of what happens in my case. Anyway, my way of solving it is to setup the proxy server in the app...

I don't use synaptic, I rather like cli tools so I stick to apt-get. I'm not sure right now how to set it up in synaptic (im using kubuntu) but I would guess it's somewhat intuitive...

---

### Post by tropdoug on 2008-05-20
Not sure about the webproxy thing, you will have to explain what exactly that is. But I dont think I have one anyway! 

interestingly I tried sudo apt-get update and this is the code that returned


```
kim@laptop:~$ sudo apt-get update
0% [Connecting to debian.charite.de (1.0.0.0)] [Connecting to archive.canonical.com (1.0.0.0)]
kim@laptop:~$ 

```I don't know where but I have seen this 1.0.0.0 thing talked about when I first came onto ubuntu a couple of months ago. Obviously there is a wrong ip address in some file. 
time to do some searching

---

### Post by Maestro23 on 2008-05-20
Can you post your **/etc/apt/sources.list**

> cat /etc/apt/sources.list

---

### Post by tropdoug on 2008-05-20
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://debian.charite.de/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://debian.charite.de/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://debian.charite.de/ubuntu/ gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://debian.charite.de/ubuntu/ gutsy-security multiverse
```
The debian.charite.de server is just the latest of the ones I have tried as apparently the best one at that moment, but I have tried the main one, and all the Aussie ones. On my desktop machine, I am using "Custom servers" which I cannot find anywhere, so not sure how I got that. 

As you can see all deb lines are uncommented

---

### Post by EXCiD3 on 2008-05-20
Go to System > Administration > Software Sources and use the Select Best Server option to find one that works best for your location.

---

### Post by Maestro23 on 2008-05-20
EXCiD beat me to it. :smile:

---

### Post by tropdoug on 2008-05-20
already done that as in my original post, numerous times. Its not the server. What happens is that whichecver server is picked, the reload will connect and download mayeb ten packages, then fail the rest. I close synaptic, open it again, select the best server again, (it often is a different one) and the same thing happens. 

See the Code return from my post for apt-get update which includes the line with the IP address as 1.0.0.0. I am sure that that is the problem, but I don't know where or how my machine is pointing to a non existant IP address. 

Any other ideas anyone?

---

### Post by tropdoug on 2008-05-20
BUMP 
Now I understand, 

whatever file makes synaptic connect to the selected server, has a fault. It is (in my case) pointing to a server at IP address 1.0.0.0 which should be 'mirror.optus.net' in fact that servers IP address is 211.29.132.173 

So what I guess I need to do, is find out why synaptic is unable to correctly point to the right IP address, and indeed apt-get also suffers the same problem. 

Does anyone know the file concerned?

---

### Post by tropdoug on 2008-05-20
This is weird answering myself, hope I don't start arguing! 

Okay I am pretty certain I solved it. So for any others experiencing this here is what I did. 

I am using the mirror.optus.net server. I found a site [COLOR=Blue]http://www/hcidtata.info/host2ip.cgi [/COLOR]and put in the server name and found out it's IP address ([COLOR=Blue]211.29.132.173[/COLOR]) I then did the same for archive.canonical.com which is IP address ([COLOR=Blue]91.189.90.142[/COLOR] ) I then did in a terminal

sudo gedit /etc/apt/sources.list 

then using the [COLOR=Blue]replace[/COLOR] function in the editor, I found all references to both hostnames and replaced them with the appropriate IP address, and saved it (having saved the original as sourcesold.list)

then back to the terminal, and 

[COLOR=Blue] sudo apt-get update [/COLOR]

all went well

[COLOR=Blue] sudo apt-get upgrade[/COLOR]

and as I speak the packages are being upgraded. So I will wait for them to finish, try a few other things I want to install and if all is well will mark this thread solved. 

If any admin guys catch this thread, is it worth maybe making it a sticky, because I could find very little addressing this, but quite a few with similar if not the same issue, and perhaps someone can explain to me how or why this happens after a clean install?

Thanks all. :-)

---

