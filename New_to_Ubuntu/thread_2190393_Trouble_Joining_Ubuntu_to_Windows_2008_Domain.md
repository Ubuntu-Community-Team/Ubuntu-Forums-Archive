---
title: "Trouble Joining Ubuntu to Windows 2008 Domain"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by felayusuf on 2013-11-27
Hi all, I am a new linux user with absolutely no experience before now.
I just installed Ubuntu 12.04 desktop for learning purposes but I cannot join it to a domain.

I have read about users with issues close to mine get solutions from this forum, even I have tried some of those solutions.

I still cannot join the system to the domain, please help

see below the prompt I get when I try running sudo apt-get install likewise-open5


sudo apt-get install likewise-open5
[sudo] password for olufela: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package likewise-open5

---

### Post by felayusuf on 2013-11-28
HI all, it's been almost 2 days since I posted this problem (Trouble joining Ubuntu 12.04 to Windows 2008 domain yet no one has responded.

I need your help urgently on this issue.

Thanks

---

### Post by coldraven on 2013-11-28
Sorry but I'm not an expert in this field but is this link of any help?
Towards the bottom it shows joining to a Windows machine (Fig. 12)
[http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/](http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/)

---

### Post by coldraven on 2013-11-28
Sorry but I'm not an expert in this field but is this link of any help?
Towards the bottom it shows joining to a Windows machine (Fig. 12)
[http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/](http://www.unixmen.com/howto-install-and-configure-samba-share-in-ubuntu/)

---

### Post by sotiris2 on 2013-11-28
What version of Ubuntu are you running. And do you have an active internet connection on that Ubuntu machine?

---

### Post by felayusuf on 2013-11-29
Hi Sotiris2, thanks for looking in.

My ubuntu version is 12.04 LTS Desktop and yes I have an active interrnet connection on the system.

---

### Post by felayusuf on 2013-11-29
Hi Coldraven, thanks for the link, I tried it but see the results that I got below;

sudo apt-get  install  samba samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  samba-common-bin smbclient samba-common

E: Package 'samba' has no installation candidate

---

### Post by squakie on 2013-11-29
oooppppssss - guess I accidentally posted in the middle of my reply - please my next post.

---

### Post by squakie on 2013-11-29
Try installing Synaptic Package Manager:  sudo apt-get install synaptic 

Then start Synaptic via the menus or via sudo synaptic in a terminal.

Use the search box and put in samba

Besides samba-common, does samba show in that list?

What specific, if any, instructions have you tried so far and did any of those have you edit /etc/apt/sources.list?

The only instructions I could find for liveopen5 are  for a quite old version of Ubuntu.  One thing mentioned there is that it requires the "universe" source being enabled.  DId you do that?  Perhaps the package is not available for up-to-date Ubuntu - I don't know as I had never heard of it until this thread.

---

### Post by squakie on 2013-12-01
[QUOTE=felayusuf;12860632....
However the following packages replace it:
  samba-common-bin smbclient samba-common

E: Package 'samba' has no installation candidate[/QUOTE]

BTW - did you try sudo apt-get install samba-common-bin smbclient samba-common as the output showed?

---

### Post by squakie on 2013-12-07
BTW - I had *no luck* in getting an Ubuntu box and 2 Raspberry Pi's to join a Windows network.  Turns out the Ubuntu box at the time (a ZBox) apparently through some sort of algorythm somewhere decided it needed to drop the wireless for a few seconds when ilde and then reconnect it.  That box is now gone and I'm using a home-brew "normal" desktop with Ubuntu and the same 2 Pi's.  No troubles now at all.  Once it a great while on of the Pi's won't accept ssh (I believe it's reaching a time out) so I try ping and find out it's gone from arp.  A second set of pings sets things right and all is well in the world  Happens very rarely.  I also don't have Samba set up as servers on either of the Pi's right now - just clients - so trying to open the windows network just results in no shares being found.

---

