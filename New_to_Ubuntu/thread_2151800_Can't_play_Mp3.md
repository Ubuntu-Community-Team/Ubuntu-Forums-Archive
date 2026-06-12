---
title: "Can't play Mp3"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by angrygamer on 2013-06-05
I can't, so installed VLC, and VLC installed all the additional codecs, I try playing it with VLC, Rythbox, but none on them work. HHELLPP!!!!

I also tried playing an .avi file and it played just fine but the MP#'s are messing up! It wont even play.

---

### Post by 3rdalbum on 2013-06-05
Ubuntu doesn't come with MP3 playback support. It is easy to install, although I can't remember the exact name of the package.

In Ubuntu Software Center, install a package named (something like) gstreamer0.10-plugin-fluendo-mp3

---

### Post by angrygamer on 2013-06-05
I looked and it says I have to pay 35 DOLLARS CAN i PLEASE have a free way.

---

### Post by Annadin on 2013-06-05
Open it with rhythm box, then try and play it, it should come with a pop up that asks Ubuntu can't play mp3s, and it has an option to search for the correct plugin, my plug-ins where called GStreamer extra plug-ins and GStreamer ffmpeg video plugin, they were free

---

### Post by BBQdave on 2013-06-05
> **angrygamer said:**
> I looked and it says I have to pay 35 DOLLARS CAN i PLEASE have a free way.

You want **GStreamer extra plugins** - it's free.

---

### Post by 3rdalbum on 2013-06-06
> **angrygamer said:**
> I looked and it says I have to pay 35 DOLLARS CAN i PLEASE have a free way.

The MP3 decoder is free. You are probably looking at the full, licensed codex bundle. Just look for the MP3 codex by itself.

---

### Post by newb85 on 2013-06-06
Look for Ubuntu Restricted Extras.  It's free.  It includes the codecs for .mp3, along with several other similar things you'll probably want down the road.

---

### Post by andrew.46 on 2013-06-06
I suspect that vlc might use a shared libavcodec so all that is probably required is the version of libavcodec that has *not* been stripped as much by the packagers. For Raring this is:

```

sudo apt-get install libavcodec-extra-53

```

and this might be enough to get your mp3s going...

---

### Post by mc4man on 2013-06-06
> **andrew.46 said:**
> I suspect that vlc might use a shared libavcodec so all that is probably required is the version of libavcodec that has *not* been stripped as much by the packagers. For Raring this is:
...
and this might be enough to get your mp3s going...
What I see here (messages or cli) for mp3 in vlc
> [0x7fcaecc055d8] main decoder debug: using decoder module "mpeg_audio"

Seems external to avcodec?
Generally when someone installs vlc or even repo mplayer & can't play a file, then I'd suspect the file, not libraires/packages whatever.
(either their player version doesn't support or if it does, the file itself.

vlc -vvv & then play .mp3 should prove informative

---

### Post by cincinnatus13 on 2013-06-06
First, just do ```
sudo apt-get install ubuntu-restricted-extras
```.
That'll help regardless unless you're completely and utterly devoted to only open source items.

---

