---
title: "HOWTO: Install KTorrent 2.0beta1"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by psychicdragon on 2006-06-04
Since KTorrent is the best torrent client for GNU/linux and the package in Dapper is out of date. I thought I'd try my hand at building the latest version and of course share it with anyone who wants it. :KS 

This is built for i386. If you use another architecture, I can provide the debianized source so you can build it yourself.

Here we go...
[LIST=1]
[*]Download this file: [http://members.shaw.ca/davekeogh/misc/ktorrent_2.0beta1_i386.deb](http://members.shaw.ca/davekeogh/misc/ktorrent_2.0beta1_i386.deb)
[*]Install it: ```
sudo dpkg -i ktorrent_2.0beta1_i386.deb
```
[/LIST]
That's it.

---

### Post by johanvrt on 2006-06-05
Great! Thanks !

---

### Post by Rizado on 2006-06-05
Very nice.
I've enabled DHT and all but when I look at the peer tab it's a red cross in the DHT column next to the peers. Does it have to be enabled on the tracker too?

---

### Post by caldevil on 2006-06-05
thanks.
Can you or anyone else also build kopete 0.12? I am too lazy to download all the development files for kde (as I don't use many kde applications) and build myself.

---

### Post by psychicdragon on 2006-06-05
[QUOTE=Rizado]Very nice.
I've enabled DHT and all but when I look at the peer tab it's a red cross in the DHT column next to the peers. Does it have to be enabled on the tracker too?[/QUOTE]
I'm really not sure. I don't even know what DHT is. :rolleyes: 
It's marked (EXPERIMENTAL), so it may not even work?

---

### Post by psychicdragon on 2006-06-05
[QUOTE=caldevil]thanks.
Can you or anyone else also build kopete 0.12? I am too lazy to download all the development files for kde (as I don't use many kde applications) and build myself.[/QUOTE]
Sure, I'll try and do it for you when I get back from class. :KS

---

### Post by stoeptegel on 2006-06-05
[QUOTE=Rizado]Very nice.
I've enabled DHT and all but when I look at the peer tab it's a red cross in the DHT column next to the peers. Does it have to be enabled on the tracker too?[/QUOTE]

No DHT has it's own network with peers after you've bootstrapped into the network. The only rule is that a client shouldn't use DHT for a torrent when it has a "private" flag. (you can see that checkbox option when you make a torrent in KTorrent)

These red crosses in the DHT column could  be because:
1) DHT is disabled in preferences
2) There are no peers in swarm that support the official mainline DHT.

AFAIK these icon for DHT is only an indication that this peer supports DHT. 
It's not telling you that the connection is established by DHT or not.

---

### Post by ZZambia on 2006-06-05
[QUOTE=psychicdragon]Sure, I'll try and do it for you when I get back from class. :KS[/QUOTE]

Don't worry... I've already done it.

[Please read post on Kubuntu Forum]("http://kubuntuforums.net/forums/index.php?topic=5727.0")

Also, I've post a new topic on this forum room, i'm just waiting for moderator to apply.

Cheers

---

### Post by johanvrt on 2006-06-06
[QUOTE=ZZambia]Don't worry... I've already done it.

[Please read post on Kubuntu Forum]("http://kubuntuforums.net/forums/index.php?topic=5727.0")

Also, I've post a new topic on this forum room, i'm just waiting for moderator to apply.

Cheers[/QUOTE]

This one for kopete might be better (does not break anything) afaIk, and works perfect on my pc :)

[http://www.ubuntu-zh.org/~freeflying/packages/kopete_3.5.3kopete0.12.0-1_i386.deb](http://www.ubuntu-zh.org/~freeflying/packages/kopete_3.5.3kopete0.12.0-1_i386.deb) 

I used wget to download it

---

### Post by ZZambia on 2006-06-06
It's quite hard to download. BTW, I have resolved (version) issues and I'm approaching to make an AMD64 DEB too. Stay tuned.

For thread master: how did you post this thread in this forum room? I'm trying in posting a thread for two days, but with no luck (everything was ok, but I don't see my thread in list). Thanks

---

### Post by psychicdragon on 2006-06-06
[QUOTE=ZZambia]It's quite hard to download. BTW, I have resolved (version) issues and I'm approaching to make an AMD64 DEB too. Stay tuned.

For thread master: how did you post this thread in this forum room? I'm trying in posting a thread for two days, but with no luck (everything was ok, but I don't see my thread in list). Thanks[/QUOTE]
I think one of the moderators has to review your post first. It may end up taking a little while... You could always send one of them a PM and ask them to take a look at it?

---

### Post by Rizado on 2006-06-11
Alright everyone, DHT works. Today I saw "DHT: got getPeers request" in the log so I checked the peer list and there it was, two green marks. Both of them were from the official BitTorrent client so I guess it's not many that have DHT enabled.

---

### Post by tUrtleAE86 on 2006-06-11
THANK YOU! Man, I was having some serious issues with KTorrent 1.2
It was uploading around 60-80 Kb/s even when I set it to 20 K/s. And, my downloads were going nowhere.

2.0 works great, though. :)

---

### Post by stoeptegel on 2006-06-12
Excuse me guys.
In my previous post i said that DHT works with bootstrapping into the network, but this is not the case anymore with the newest DHT protocol. 

Now there's a bit in the handshake that says if the other peer supports DHT or not, and from here you find other nodes for the torrent.

---

### Post by psychicdragon on 2006-06-12
[QUOTE=stoeptegel]Excuse me guys.
In my previous post i said that DHT works with bootstrapping into the network, but this is not the case anymore with the newest DHT protocol. 

Now there's a bit in the handshake that says if the other peer supports DHT or not, and from here you find other nodes for the torrent.[/QUOTE]
Yep, KTorrent 2.0 supports the newer DHT protocol, while most Windows clients do not yet (uTorrent for one). This is quite possibly why very few peers show up as DHT enabled. 

It seems almost 50% of peers are using uTorrent which doesn't set the DHT bit in the handshake, which means they won't show up as a DHT node in KTorrent. Not sure about BitComet either, which is the other most used closed-source client.

References:
[http://ktorrent.pwsp.net/forum/viewtopic.php?t=505](http://ktorrent.pwsp.net/forum/viewtopic.php?t=505)
[http://forum.utorrent.com/viewtopic.php?id=10655](http://forum.utorrent.com/viewtopic.php?id=10655)

---

### Post by ububaba on 2006-06-12
For some odd reason KTorrent 1.2 refuses to start. I have used it for quite some time.
No execuses provided for the failure.

---

### Post by CronoDekar on 2006-06-12
Something I was wondering about KTorrent... does it have a feature to end seeding once I hit a certain ratio?  I've got limited monthly bandwidth, so I unfortunately cannot afford to leave a torrent going overnight.  The scheduler looks cool with being able to set up bandwidth limits at certain times, but isn't exactly what I'm looking for.

It looks like a neat bittorent client that already satisfies one of my requirements (is lightweight) -- now I just need that other one.

---

### Post by mjm115 on 2006-06-12
Does this version fix the whole "stalled" torrent issue?  Whenever I load a torrent, it doesn't download, but stays at "stalled".  Has this been resolved?

---

### Post by psychicdragon on 2006-06-12
[QUOTE=mjm115]Does this version fix the whole "stalled" torrent issue?  Whenever I load a torrent, it doesn't download, but stays at "stalled".  Has this been resolved?[/QUOTE]
I haven't had this bug occur in 2.0beta, but I found it quite prevalent in 1.2. That said there has been at least one report of stalled torrents on the KTorrent forum (see [this post]("http://ktorrent.pwsp.net/forum/viewtopic.php?t=549")). I think this bug should be completely squashed by 2.0, but is essentially a non-issue, for me at least, in the current version.

---

### Post by psychicdragon on 2006-06-12
[QUOTE=CronoDekar]Something I was wondering about KTorrent... does it have a feature to end seeding once I hit a certain ratio?  I've got limited monthly bandwidth, so I unfortunately cannot afford to leave a torrent going overnight.  The scheduler looks cool with being able to set up bandwidth limits at certain times, but isn't exactly what I'm looking for.

It looks like a neat bittorent client that already satisfies one of my requirements (is lightweight) -- now I just need that other one.[/QUOTE]
Nope, 2.0beta1 doesn't have this feature. Perhaps a post on the KTorrent forums is in order? This seems like a fairly important missing feature.

---

### Post by Rizado on 2006-06-12
[QUOTE=psychicdragon]Nope, 2.0beta1 doesn't have this feature. Perhaps a post on the KTorrent forums is in order? This seems like a fairly important missing feature.[/QUOTE]I'm pretty sure it does. I think I remember seeing this one somewhere in the settings, maybe torrent specific.

EDIT: Yup there it is, under status to the right there is a box called "Use limit" or something like that, English is not my native language.

---

### Post by CronoDekar on 2006-06-12
[QUOTE=psychicdragon]Nope, 2.0beta1 doesn't have this feature. Perhaps a post on the KTorrent forums is in order? This seems like a fairly important missing feature.[/QUOTE]

[Done](http://ktorrent.org/forum/viewtopic.php?p=3455)!  Thanks for the info!

---

### Post by psychicdragon on 2006-06-12
[QUOTE=Rizado]I'm pretty sure it does. I think I remember seeing this one somewhere in the settings, maybe torrent specific.

EDIT: Yup there it is, under status to the right there is a box called "Use limit" or something like that, English is not my native language.[/QUOTE]
Hey, you're right. :rolleyes: I never noticed it down there, it's pretty well hidden. I assumed it would be an application-wide setting, but it makes sense per-torrent as well.

---

### Post by ivasic on 2006-06-12
KTorrent has an option to stop seeding after you hit specified ratio.

It's not global, but per torrent. You'll find it in InfoWidget, but first enable that plugin in Settings.

---

### Post by CronoDekar on 2006-06-12
Well *now* you tell me! ;)

---

### Post by ivasic on 2006-06-12
Sorry :)

---

### Post by caldevil on 2006-06-12
I am having some problems using this deb package. All browsers were taking considerably longer time to resolve address using this. I compiled the source package myself and things look fine now. I wonder what the problem may be.

---

### Post by JPatrick on 2006-06-13
Uploaded here:

[http://www.kubuntu-es.org/jpatrick/pub/ktorrent_2.0beta1_i386.deb](http://www.kubuntu-es.org/jpatrick/pub/ktorrent_2.0beta1_i386.deb)

---

### Post by msak007 on 2006-06-15
Thanks for the package. When I tried to compile from source, everytime I tried to install it using checkinstall it would fail. The error was something about an error occured while trying to overwrite the file /usr/share/mimelnk/application/x-bittorrent.desktop because it was part of kdelibs-data. Did you get the same error at any point?

---

### Post by psychicdragon on 2006-06-15
[QUOTE=msak007]Thanks for the package. When I tried to compile from source, everytime I tried to install it using checkinstall it would fail. The error was something about an error occured while trying to overwrite the file /usr/share/mimelnk/application/x-bittorrent.desktop because it was part of kdelibs-data. Did you get the same error at any point?[/QUOTE]I removed that file from the package because the version provided by kdelibs-data is functionally the same but has more translations in it.

---

### Post by ububaba on 2006-06-15
[QUOTE=JPatrick]Uploaded here:

[http://www.kubuntu-es.org/jpatrick/pub/ktorrent_2.0beta1_i386.deb](http://www.kubuntu-es.org/jpatrick/pub/ktorrent_2.0beta1_i386.deb)[/QUOTE]
Every time I try, the server can not be found. Invalid URL?:sad:

---

### Post by msak007 on 2006-06-15
[QUOTE=psychicdragon]I removed that file from the package because the version provided by kdelibs-data is functionally the same but has more translations in it.[/QUOTE]

Just for future reference, how did you do that? Was it during the configure or compile stage? I checked ./configure help to see if there were any extra options or flags but didn't see any like that. Any help would be appreciated.

---

### Post by psychicdragon on 2006-06-16
[QUOTE=msak007]Just for future reference, how did you do that? Was it during the configure or compile stage? I checked ./configure help to see if there were any extra options or flags but didn't see any like that. Any help would be appreciated.[/QUOTE]
I basically just deleted a line in the Makefile.

---

### Post by msak007 on 2006-06-19
I see...well thanks for the info I'll keep that little trick in mind. Thanks again for the package ktorrent 2 rocks.

---

### Post by NeoChaosX on 2006-06-19
The Rapidshare link doesn't work anymore, and JPatrick's mirror on kubuntu-es.org doesn't work either. Anybody else have a mirror for the deb?

---

### Post by psychicdragon on 2006-06-21
[QUOTE=NeoChaosX]The Rapidshare link doesn't work anymore, and JPatrick's mirror on kubuntu-es.org doesn't work either. Anybody else have a mirror for the deb?[/QUOTE]
Hi,

I'm not at home right now. I'll re-upload it when I get home tonight. I just switched ISP's recently so I should be able to upload it to a more permanent host this time.

---

### Post by psychicdragon on 2006-06-21
Okay, I uploaded the file to my new webspace. You can grab it here: 
[http://members.shaw.ca/davekeogh/misc/ktorrent_2.0beta1_i386.deb](http://members.shaw.ca/davekeogh/misc/ktorrent_2.0beta1_i386.deb)

:KS I also updated the top post.

---

### Post by bionnaki on 2006-06-28
thanks
works with oink,finally, btw.

---

### Post by Enigmatic on 2006-06-30
Is anyone else noticing very erratic speeds? Mine can jump by +- 100KB/s in a few seconds sometimes.

---

### Post by Don_DiZzLe on 2006-07-01
Will this also work for Ubuntu with Gnome?

---

### Post by psychicdragon on 2006-07-01
[QUOTE=Don_DiZzLe]Will this also work for Ubuntu with Gnome?[/QUOTE]
Yes. You'll have to run **sudo apt-get -f install** after installing the package to get all the dependencies though.

It requires kdelibs and probably some other stuff, so it will take up several megabytes of hard-drive space.

---

### Post by Don_DiZzLe on 2006-07-01
Ok cool I just did that, but the KTorrent icon is not displayed right, how do i correct it?

---

### Post by psychicdragon on 2006-07-01
[QUOTE=Don_DiZzLe]Ok cool I just did that, but the KTorrent icon is not displayed right, how do i correct it?[/QUOTE]
I'm afraid I don't quite understand what you mean by this. Could you please clarify?

---

### Post by stoeptegel on 2006-07-18
I noticed KTorrent 2.0RC1 is just released guys, get it while it's hot :)

---

### Post by psychicdragon on 2006-07-18
> **stoeptegel said:**
> I noticed KTorrent 2.0RC1 is just released guys, get it while it's hot :)
Is the Kubuntu package on their site a checkinstall package like the 2.0beta1? I'm on a non-Debian machine right now so I can't check it out myself...

---

### Post by stoeptegel on 2006-07-18
> **psychicdragon said:**
> Is the Kubuntu package on their site a checkinstall package like the 2.0beta1? I'm on a non-Debian machine right now so I can't check it out myself...

Yes i think it is.

---

### Post by ivasic on 2006-07-18
It is but you can check out this URL for packages created by Kubuntu package managers (can I say official ones?):

[http://dev.bit-freaks.net/apachelogger/deb/ktorrent/](http://dev.bit-freaks.net/apachelogger/deb/ktorrent/)

Only i386 are available but x64 is expected to be out soon too. Anyway, KTorrent website will be updated soon so keep an eye on it.

---

### Post by eXCeSS on 2006-07-18
```
andrew@linux-laptop:~$ sudo dpkg -i ktorrent_2.0rc1-1_i386.deb
(Reading database ... 117996 files and directories currently installed.)
Unpacking ktorrent (from ktorrent_2.0rc1-1_i386.deb) ...
dpkg: error processing ktorrent_2.0rc1-1_i386.deb (--install):
 trying to overwrite `/usr/share/mimelnk/application/x-bittorrent.desktop', which is also in package kdelibs-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ktorrent_2.0rc1-1_i386.deb

```

On kubuntu 6.06 using the .debs.
Any help?

edit:
Problem fixed by using the .deb from [http://dev.bit-freaks.net/apachelogger/deb/ktorrent/](http://dev.bit-freaks.net/apachelogger/deb/ktorrent/)

---

### Post by eXCeSS on 2006-08-09
2.0 is out! Anyone have a .deb to install it :D

---

### Post by Patskumaster on 2006-08-09
> **eXCeSS said:**
> 2.0 is out! Anyone have a .deb to install it :D
I try soon compiling source-code.:p

---

### Post by Patskumaster on 2006-08-14
KTorrent 2.0 Deb is available!

[http://ktorrent.org/downloads/2.0/ktorrent-2.0-i386.deb](http://ktorrent.org/downloads/2.0/ktorrent-2.0-i386.deb)

---

### Post by Enigmatic on 2006-08-14
Having a small problem installing it. I removed ktorrent (the beta) from Synaptec, and when installing the .deb I got this error:

dpkg: error processing ktorrent-2.0-i386.deb (--install): trying to overwrite /usr/share/mimelnk/application/x-bittorrent.desktop', which is also in package kdelibs-data.

---

### Post by ububaba on 2006-08-14
Me too got the same message!

---

### Post by npu on 2006-08-14
> **Enigmatic said:**
> Having a small problem installing it. I removed ktorrent (the beta) from Synaptec, and when installing the .deb I got this error:

dpkg: error processing ktorrent-2.0-i386.deb (--install): trying to overwrite /usr/share/mimelnk/application/x-bittorrent.desktop', which is also in package kdelibs-data.
This worked for me:

First remove your old version of KTorrent (if you have one installed).
```
sudo apt-get remove ktorrent
```
Then force install the new version.
```
sudo dpkg -i --force-overwrite ktorrent-2.0-i386.deb
```
That should do it.

---

### Post by Patskumaster on 2006-08-15
> **npu said:**
> This worked for me:

First remove your old version of KTorrent (if you have one installed).
```
sudo apt-get remove ktorrent
```
Then force install the new version.
```
sudo dpkg -i --force-overwrite ktorrent-2.0-i386.deb
```
That should do it.

That works! Very nice, Thanks!

---

### Post by TSP on 2006-08-24
Hi! I just compile the last SVN snapshot and works great for me. i upload it in electronic files and that's the reason why i rename the file extension, they don't allow .deb files.

```

http://www.electronicfiles.net/files/4308/ktorrent-23-08-06_06-1_i386.tar
```

Please post feedback so i can keep making deb files of this great client. Cheers!

---

### Post by Weav on 2006-08-31
I've tried restarting installation of Ktorrent but keep on getting errors and it just won't let me get rid of it.

```

steve@steve-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kdelibs-data
The following NEW packages will be installed:
  kdelibs-data
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/7084kB of archives.
After unpacking 28.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 81387 files and directories currently installed.)
Unpacking kdelibs-data (from .../kdelibs-data_4%3a3.5.2-0ubuntu18.1_all.deb) ...dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5.2-0ubuntu18.1_all.deb (--unpack):
 trying to overwrite `/usr/share/mimelnk/application/x-bittorrent.desktop', which is also in package ktorrent-2.0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.2-0ubuntu18.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any Ideas? thanks

---

### Post by msak007 on 2006-08-31
> **Weav said:**
> I've tried restarting installation of Ktorrent but keep on getting errors and it just won't let me get rid of it. Any Ideas? thanks
I had the same problem trying to upgrade to the latest version when I downloaded the newest .deb from the ktorrent web site. I remember that psychicdragon did something with that file to get the beta to compile at the time because it wouldn't let you overwrite it (I asked about it, it's way back in the thread). Try renaming the file to something like "x-bittorrent.desktop_backup" and try again:
```
cd /usr/share/mimelnk/application/
sudo mv x-bittorrent.desktop x-bittorrent.desktop_backup
```[FONT=monospace][/FONT]
Then try to reinstall kdelibs-data and ktorrent and see if that works.

---

### Post by Weav on 2006-08-31
> **msak007 said:**
> I had the same problem trying to upgrade to the latest version when I downloaded the newest .deb from the ktorrent web site. I remember that psychicdragon did something with that file to get the beta to compile at the time because it wouldn't let you overwrite it (I asked about it, it's way back in the thread). Try renaming the file to something like "x-bittorrent.desktop_backup" and try again:
```
cd /usr/share/mimelnk/application/
sudo mv x-bittorrent.desktop x-bittorrent.desktop_backup
```[FONT=monospace][/FONT]
Then try to reinstall kdelibs-data and ktorrent and see if that works.
Hmmmm still did not fix it. I renamed the x-bittorrent.desktop but yet it's still referencing it? It doesn't even really make any sense.

Any other ideas on how to fix this? Thanks

---

### Post by foxy123 on 2006-08-31
I use ktorrent 2.0.1 from Dapper Backports. Why do you need debs?

---

### Post by sunil.sundareswaran on 2007-09-05
> **npu said:**
> This worked for me:

First remove your old version of KTorrent (if you have one installed).
```
sudo apt-get remove ktorrent
```
Then force install the new version.
```
sudo dpkg -i --force-overwrite ktorrent-2.0-i386.deb
```
That should do it.
______________________________________________________________________

Hey there, 

                       M new to ubuntu well actually i was trying to install KTorrent application as mentioned there were no errors during the installation but m not able to get an idea about how to start the application. Can anyone guide me I ll give the responses as shown  during the installation .......

Selecting previously deselected package ktorrent-2.0.
(Reading database ... 88002 files and directories currently installed.)
Unpacking ktorrent-2.0 (from ktorrent-2.0-i386.deb) ...
Setting up ktorrent-2.0 (2.0-1) ...

Well is there anything else to follow also how can i find the same ...... please do guide me as I m new to linux. :lolflag:

Regards,
Sunil.:)

---

