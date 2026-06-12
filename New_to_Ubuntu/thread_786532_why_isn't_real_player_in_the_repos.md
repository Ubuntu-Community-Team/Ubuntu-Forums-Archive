---
title: "why isn't real player in the repos?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-08
why?

---

### Post by billgoldberg on 2008-05-08
Might be because it's considered by some as a spyware on windows.

The player itself is only good for playing rmvb files, and vlc does a great job at playing those.

Also when I installed real player, it changed all my audio icons to "real player" (windows behavior !!!) and it was a pain in to a*ss to change them back.

---

### Post by lunaluna on 2008-05-08
> **billgoldberg said:**
> Might be because it's considered by some as a spyware on windows.

The player itself is only good for playing rmvb files, and vlc does a great job at playing those.

Also when I installed real player, it changed all my audio icons to "real player" (windows behavior !!!) and it was a pain in to a*ss to change them back.

did you actually played rmvb files with vlc because  until now i could only have the sound but not picture
how did you do it?

---

### Post by Tatty on 2008-05-08
Try the helix player.  It is a community supported version of realplayer... infact I think the official linux realplayer is based on the helix player.

I think realplayer is in the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos if you want it.

---

### Post by lunaluna on 2008-05-08
> **Tatty said:**
> Try the helix player.  It is a community supported version of realplayer... infact I think the official linux realplayer is based on the helix player.

I think realplayer is in the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos if you want it.

it also has all the "real" codecs too i supose...?
so if i install it i play the "real" files...

---

### Post by parish on 2008-05-08
> **Tatty said:**
> Try the helix player.  It is a community supported version of realplayer... infact I think the official linux realplayer is based on the helix player..
I'm trying to install Realplayer too. Several hits I found on Google led nowhere, describing old versions of Ubuntu and/or realplayer, or download links not working.

So, I searched here, found this thread, took your advice to install Helix.....but it says it can't play Real files (.rm) Huh? :confused: Click the Check For Updates button (in Helix) and it took me to Real's website where I downloaded a .bin and a .rpm version of Realplayer v11, but Ubuntu doesn't seem to know what to do with either of them.

Can you help either getting Helix (which I'd rather use) to play Real files, or to help install the Realplayer I've downloaded. Thanks.

---

### Post by Sephyryx on 2008-05-15
[https://player.helixcommunity.org/Index.html](https://player.helixcommunity.org/Index.html)

There's a link.

---

### Post by niteshifter on 2008-05-15
Hi,

You can download Real Player 10 (Gold) as a .deb from:
[debian-multimedia.org]("http://debian-multimedia.org/dists/stable/main/binary-i386/package/realplayer.php")

The file name and page text states it is version 10.0.9-0.1, what you get is 10.0.9.809

---

### Post by Xiong Chiamiov on 2008-05-15
> **parish said:**
> I'm trying to install Realplayer too. Several hits I found on Google led nowhere, describing old versions of Ubuntu and/or realplayer, or download links not working.

So, I searched here, found this thread, took your advice to install Helix.....but it says it can't play Real files (.rm) Huh? :confused: Click the Check For Updates button (in Helix) and it took me to Real's website where I downloaded a .bin and a .rpm version of Realplayer v11, but Ubuntu doesn't seem to know what to do with either of them.

Can you help either getting Helix (which I'd rather use) to play Real files, or to help install the Realplayer I've downloaded. Thanks.
Don't install .rpm's unless you have no other choice (they're meant for Red Hat-based distros).  The order you're looking for is Synaptic -> .deb -> source (usually tar.gz) -> .bin -> .rpm.  The bin file should work fine after you give it permissions to execute (chmod +x [filename] in terminal, or right-click -> properties -> permissions).

That all said, give [this guide]("http://monkeyblog.org/ubuntu/installing/") a good read, and keep it bookmarked.

---

