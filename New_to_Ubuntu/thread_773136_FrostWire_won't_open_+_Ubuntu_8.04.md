---
title: "FrostWire won't open + Ubuntu 8.04"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-28
I am running Ubuntu 8.04 and I can not get Frostwire to open.  There is an icon in my applications menu but when I click on it nothing happens.

Any suggestions?

---

### Post by bamend on 2008-04-28
I had the same problem with it.  It messed up my ntfs drives.  I ended up deleting it and installing limewire.

---

### Post by barney385 on 2008-04-28
Use Deluge

---

### Post by tango_ninja on 2008-04-28
I've heard of a lot of frostwire problems...I could never get it working on 7.10 (Something about the correct version of Java needed, and the correct version was an *older* version).

I ended up getting rid of it and installing limewire, then migrating to deluge.

---

### Post by saskatchewan on 2008-04-28
How do I search with deluge?

---

### Post by tango_ninja on 2008-04-28
deluge is slightly different than gnutella-p2p apps since it uses torrents. basically you configure which torrent sites you want to download files from (bit torrent, piratebay, torrentspy etc) and you search using the search bar top middle of the app ([http://deluge-torrent.org/images/detail.png](http://deluge-torrent.org/images/detail.png))

---

### Post by barney385 on 2008-04-28
Deluge has some nice plug-ins available and good support also.

---

### Post by saskatchewan on 2008-04-28
Okay, I found deluge, now how do I get rid of frostwire?

I tried looking in the add remove menu and I can't find it...

Suggestions?

---

### Post by jacob01 on 2008-04-28
you need java run time

to install java
sudo apt-get install sun-java6-jre

---

### Post by evozniak on 2008-04-28
try to launch frostwire from console and post here the output messages

from console type > frostwire

---

### Post by tango_ninja on 2008-04-28
for removing frostwire.....did you look in Synaptic?

you can (hopefully) remove it with the following code in terminal:
```
sudo apt-get remove frostwire
```

if you want to **completely** remove frostwire use:
```
sudo apt-get --purge remove frostwire
```

post any problems

---

### Post by tliotis on 2008-04-29
> **jacob01 said:**
> you need java run time

to install java
sudo apt-get install sun-java6-jre
thanks i was searching that!!:popcorn:

---

### Post by billgoldberg on 2008-04-29
Yes like someone said, you need java installed to be able to use frostwire.

The open-java package from "ubuntu-restricted-extras" doesn't work for frostiwire.

People advising to use deluge instead of frostwire really need to give better advice.

Frostwire is used to download from the gnutella network, it isn't used to download torrents (it has the capability to do so, but nobody uses it for that.)

---

### Post by linux_newf on 2008-05-03
> **billgoldberg said:**
> Yes like someone said, you need java installed to be able to use frostwire.

The open-java package from "ubuntu-restricted-extras" doesn't work for frostiwire.

People advising to use deluge instead of frostwire really need to give better advice.

Frostwire is used to download from the gnutella network, it isn't used to download torrents (it has the capability to do so, but nobody uses it for that.)

I'm installing sun-java6-jre now and in your blog you said you removed the open-java package i think.

> I had to remove the package from synaptic and install &#8220;sun-java6-jre&#8221; and the plugin from synaptic to get frostwire running.

Do you mean you removed just open-java? What plugin are you refering too?

---

### Post by mbarak on 2008-05-03
these command will remove open-java and install sun-java:
```

sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib icedtea-gcjwebplugin
sudo apt-get install sun-java6-plugin

```

---

### Post by linux_newf on 2008-05-03
Thanks dude. I have frostwire working.

Seems i can't play the file, any ideas? I guess i need to play MP3's,

Weird its working now. But i'm not complaining, :-)

---

### Post by mbarak on 2008-05-03
are you trying to play them from within frostwire? if so you have to make sure that no other programs playing sound are open.
you can configure frostwire to play your mp3's with an external player (ex: totem) from the preferences, or you can install aoss
```
sudo apt-get install alsa-oss
```
and change the shortcut for frostwire (System > Preferences > Menu) to "aoss frostwire"
this way you can use the built-in music player, and play sound in other programs (ex: rhythmbox)

if you're trying to play the mp3s from outside frostwire, you probably just need to install the right codec. when you try to play the mp3 in totem, it should ask you to install the right codec

---

### Post by linux_newf on 2008-05-03
> **mbarak said:**
> are you trying to play them from within frostwire? if so you have to make sure that no other programs playing sound are open.
you can configure frostwire to play your mp3's with an external player (ex: totem) from the preferences, or you can install aoss
```
sudo apt-get install alsa-oss
```
and change the shortcut for frostwire (System > Preferences > Menu) to "aoss frostwire"
this way you can use the built-in music player, and play sound in other programs (ex: rhythmbox)

if you're trying to play the mp3s from outside frostwire, you probably just need to install the right codec. when you try to play the mp3 in totem, it should ask you to install the right codec

I have it working, thanks again. Very nice to have a program like frostwire working with linux. First time i had one.

---

### Post by wallaper on 2008-05-09
> **mbarak said:**
> these command will remove open-java and install sun-java:
```

sudo apt-get remove openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib icedtea-gcjwebplugin
sudo apt-get install sun-java6-plugin

```

Thankyou!

Works great!

---

### Post by Argus on 2008-05-13
> **wallaper said:**
> Thankyou!

Works great!

That did the trick
TKS

---

### Post by robalcorn on 2008-05-13
I had same problem install older version i think it was 1.5

---

### Post by FOffMicrosoft on 2009-10-18
I had the java problem after updating to Frostwire 4.18.3 on Ubuntu 9.04, I got around it by rolling back the version of Frostwire to 4.17.

---

