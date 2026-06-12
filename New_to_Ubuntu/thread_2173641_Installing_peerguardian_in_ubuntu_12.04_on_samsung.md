---
title: "Installing peerguardian in ubuntu 12.04 on samsung chromebook."
date: 2013-09-10
forum: New to Ubuntu
---

### Post by steve_2 on 2013-09-10
Hi,

I have been trying to install peerguardian in ubuntu 12.04 on my samsung chromebook with no success. 
I have tried a few different instructions I have found by googling and in these forums but so far no luck.
below is basically what I have tried:

[COLOR=#000000][FONT=inherit]$ sudo apt[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000088][FONT=inherit]get[/FONT][/COLOR][COLOR=#000000][FONT=inherit] install python[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]software[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]properties
[/FONT][/COLOR][COLOR=#000000][FONT=inherit]$ sudo add[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]apt[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]repository ppa[/FONT][/COLOR][COLOR=#666600][FONT=inherit]:[/FONT][/COLOR][COLOR=#000000][FONT=inherit]jre[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000000][FONT=inherit]phoenix[/FONT][/COLOR][COLOR=#666600][FONT=inherit]/[/FONT][/COLOR][COLOR=#000000][FONT=inherit]ppa
[/FONT][/COLOR][COLOR=#000000][FONT=inherit]$ sudo apt[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000088][FONT=inherit]get[/FONT][/COLOR][COLOR=#000000][FONT=inherit] update
[/FONT][/COLOR][COLOR=#000000][FONT=inherit]$ sudo apt[/FONT][/COLOR][COLOR=#666600][FONT=inherit]-[/FONT][/COLOR][COLOR=#000088][FONT=inherit]get[/FONT][/COLOR][COLOR=#000000][FONT=inherit] install pgld pglcmd

But after the last command I get:

[/FONT][/COLOR]$ sudo apt-get install pgld pglcmd

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pgld is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


Package pglcmd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'pgld' has no installation candidate
E: Package 'pglcmd' has no installation candidate 

I have searched the forums but haven't really found anything that helps me install peerguardian. I am, of course, a complete noob at linux coming from windows. can someone help me with the installation? if there is a way to get it through software center that would be great but I don't see it there.
Thanks!

---

### Post by mikewhatever on 2013-09-10
Do you mean [this Chromebook]("http://www.google.co.il/intl/en/chrome/devices/samsung-chromebook.html") with Samsung Exynos 5 CPU? If so, then that PPA only provides packages for i386 and amd64 architectures, and you can't install them on an ARM based machine.

---

### Post by steve_2 on 2013-09-10
> **mikewhatever said:**
> Do you mean [this Chromebook]("http://www.google.co.il/intl/en/chrome/devices/samsung-chromebook.html") with Samsung Exynos 5 CPU? If so, then that PPA only provides packages for i386 and amd64 architectures, and you can't install them on an ARM based machine.


Yes that is the one...doh! Is there anyway to install peerguardian or a peerguardian like app on this chromebook? Is this chromebook not very good to use with ubuntu?

Thanks!

---

### Post by mikewhatever on 2013-09-12
You could try building PeerGuardian from source. [Here is a howto for RaspberryPi]("http://mitchtech.net/peer-guardian-on-raspberry-pi/") to get the idea of how it's done. RaspberyPi has a different ARM SoC, and runs a special Debian distro called Raspberian, so some of the required packages may have different names, but it should be similar.

---

### Post by steve_2 on 2013-09-14
> **mikewhatever said:**
> You could try building PeerGuardian from source. [Here is a howto for RaspberryPi]("http://mitchtech.net/peer-guardian-on-raspberry-pi/") to get the idea of how it's done. RaspberyPi has a different ARM SoC, and runs a special Debian distro called Raspberian, so some of the required packages may have different names, but it should be similar.


Thanks for the reply Mike...being an absolute noob I don't think I want to tackle that. I was hoping there was any easy way to get a peerguardian like solution on this chromebook. If not, as much as I like this little chromebook, I might return it while I still can. If anyone knows of an easy way to get a peerguardian like solution on an ARM samsung chromebook it would be much appreciated if you could share.

Thanks,
Steve

---

### Post by Android_63 on 2013-09-14
Are you using peerguardian for bittorrent?

---

### Post by steve_2 on 2013-09-15
> **Android_63 said:**
> Are you using peerguardian for bittorrent?


Yes.

Thanks,
Steve

---

### Post by steve_2 on 2013-09-16
Any easy solutions for getting a peerguardian like program running on samsung ARM chromebook? I have 2 days left before I have to return it.

Thanks!
Steve

---

### Post by Android_63 on 2013-09-16
> **steve_2 said:**
> Yes.

Thanks,
Steve
I use the level one blocklist from bluetack. If you care to use Transmission for bittorrent, you can just copy and paste this address into it, and you'll be safer. [http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz](http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=gz)

---

### Post by steve_2 on 2013-09-16
Thanks Android, I had looked at the blocklists and wondered if they would be enough protection. apparently they are? I'll give it a try.

Thanks,
Steve

---

### Post by fireflower on 2013-09-17
> **Android_63 said:**
> If you care to use Transmission for bittorrent... I thought Transmission was still terrible. I made a thread about it, which devolved into a "if everyone knows its terrible why is it default" exploration of the politics behind how apps get included on the live disk.

---

### Post by steve_2 on 2013-09-17
You can also install the same block list in deluge, I have read that deluge is faster than transmission?

---

### Post by fireflower on 2013-09-18
> **steve_2 said:**
> deluge is faster than transmission?Unless someone has completely re-written Transmission from the bottom  up, anything is faster than Transmission. The mail is faster than  Transmission. I use qbittorrent myself, because it works perfectly well,  and "qbit" sounds cute, and reminds me of Q*bert, from arcades in the  80's.

---

### Post by QIII on 2013-09-19
Let's not take this off track and get wrapped around the axle in a discussion about the relative merits of particular torrent clients, please.

Back to the topic.

Thanks

---

### Post by raazman on 2013-09-20
I'm not trying to be a debbie downer, but using peergaurdian or any similar application is a false sense of security. These lists are not capable of providing you with EVERY anti-p2p ip address to block. And you're not really safe unless you're using something similar to a vpn. The ip blocker applications do not work. You need to hide your ip address. Check out [Private Internet Access VPN/]("https://www.privateinternetaccess.com/"). It hides your vpn while torrenting.

---

