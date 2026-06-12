---
title: "itunes replacement"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by deptimus on 2008-07-17
hi,
what can i use to move songs to and from my ipod?

---

### Post by benfindlay on 2008-07-17
Gtkpod, for more info look [here]("http://www.gtkpod.org/about.html")

Hope this helps!

Ben

---

### Post by Frenske on 2008-07-17
Try Songbird, which is very close to iTunes and based on Firefox. It has even an add-on that makes it look like iTunes. There is also an add on for importing songs from/to iPods.
Google it since it is not in the synaptic manager.

I believe that other players might be compatible, but I suggest to try Songbird. It looks great and does everything you want from a music player.

---

### Post by Canis familiaris on 2008-07-17
Amarok syncs well with iPod I have heard. By far the best music player IMO.
Sonnbird is better iTunes in Linux. I dunno about its sync with iPod though.

---

### Post by odysseusjak on 2008-07-17
I agree with Songbird.  I use it to sync my new 8GB Nano.  The limitation to Songbird, though, is that it doesn't have 'smart playlists' yet.  You can create your regular playlist just by dragging songs to it.  When you connect your iPod, there is a button for sync.

Check out my blog for little review of it:

[http://odysseus.wordpress.com/2008/07/03/songbird/](http://odysseus.wordpress.com/2008/07/03/songbird/)

---

### Post by Promaster91 on 2008-07-17
Yea, go with Songbird. It is like a Firefox media player. You will need the "iPod Device Support" add-on located [here]("http://addons.songbirdnest.com/addon/12"). BTW, smart playlists will be supported in the next release (0.7).

---

### Post by chrisod on 2008-07-17
I use rhythmbox - works fine.

---

### Post by Raistlin82 on 2008-07-17
I've recently been trying to figure out what software is best and for me, I eventually have decided on amarok, it took a bit of getting used to, mainly because i'd only used itunes for my ipod up to now, but its workign beautifulyl now.  Its also very good at getting cover art and syncing it to your ipod as well.  Maybe thats only important to me lol!

---

### Post by deptimus on 2008-07-17
it won't let me dl songbird. it says:

/tmp/Songbird_0.6.1_linux-i686.tar-2.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences

sorry. i'm super new to this whole ubuntu thing and it's trying to dl/open it with archive manager. what should it be instead?

---

### Post by Canis familiaris on 2008-07-18
Installing Songbird:

```
wget -c ftp://ftp-mirror.internap.com/pub/www.getdeb.net/ubuntu/hardy/so/songbird_0.5-1~getdeb1_i386.deb
```

In case you have 64bit Ubuntu, replace the i386 by amd64 in each of the entries(that's what I did)

```
sudo dpkg -i songbird_0.5-1~getdeb1_i386.deb
```

Songbird would be installed.

Get the icons and set it:
```
wget -c -q http://www.psychocats.net/ubuntu/songbirdicon.png
sudo mv songbirdicon.png /usr/share/pixmaps/songbird.png
```

Run Songbird by Applications->Sound and Video->Songbird

Source: [https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

But I will still say Amarok rules.

---

### Post by SunnyRabbiera on 2008-07-18
Rhythmbox weill probably do, its usually good with ipods.
So is amarok.
But it depends on the type of ipod too, some ipods simply wont work thanks to apple being generally unfriendly to linux.

---

### Post by sloggerkhan on 2008-07-18
might try the latest banshee... I've heard it's good. I think they added a video library, too, though I can't imagine relying on gstreamer for video playback. (I'd love to see an option for a video library where you could select a player of your choice.)
[http://banshee-project.org/](http://banshee-project.org/)

---

### Post by adobrakic on 2008-07-18
I tried Amarok, and that didn't even recognize my ipod. Banshee just froze when I plugged in my ipod.

Just use GTKPod. It's not the best looking thing available, but at least it's stable. I'd get into not supporting scum corporations (i was given my ipod), but that's another story. :)

Good luck.

---

### Post by Zack McCool on 2008-07-18
I use Amarok to sync my 30GB iPod 5g, and it works like a champ...

Some newer iPods do not have any linux support yet.  Thanks, Apple...

---

### Post by SunnyRabbiera on 2008-07-18
> **adobrakic said:**
> I tried Amarok, and that didn't even recognize my ipod. Banshee just froze when I plugged in my ipod.

Just use GTKPod. It's not the best looking thing available, but at least it's stable. I'd get into not supporting scum corporations (i was given my ipod), but that's another story. :)

Good luck.

Linux applications can be trial and error, but most do the trick.

---

