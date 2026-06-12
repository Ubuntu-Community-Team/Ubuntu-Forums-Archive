---
title: "x11 support"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by vivekrocks on 2008-06-18
Hello all,

I have installed ubuntu 8.04 Hardy heron. I'm trying to install mplayer for linux on it(i'm using source). But it asks for x11 support. I hav the DVD which i downloaded from [here]("http://cdimage.ubuntu.com/dvd/current/")

And i tried installing all the packages related to x11 support from this DVD. but it still says GUI requires x11 support. Wht might be the problem please can sum1 tell me?

Thanx :)

---

### Post by RomeReactor on 2008-06-18
Hi. Try this from the terminal:
```
sudo apt-get build-dep mplayer
```
This will install the dependencies needed to compile mplayer.

Is there a particular reason you want to compile it?

---

### Post by Rocket2DMn on 2008-06-18
MPlayer doesn't need to be compiled from source anymore, see [https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer) - it's available in the repositories
Here is the very outdated page regarding compiling it from source - [https://help.ubuntu.com/community/MPlayer/Compile](https://help.ubuntu.com/community/MPlayer/Compile)

---

### Post by vivekrocks on 2008-06-18
Problem is, I do not have an internet connection on the system I want to install it. I was wondering I could get it here and install it on that system, offline!! Is there a way to do that?

---

### Post by RomeReactor on 2008-06-18
Mplayer has a lot of dependencies; if you have a friend with an internet connection (broadband, preferably), and if it's at all possible, you could take your computer to his/her house and install mplayer there. It would save you the need to find which dependencies you're missing and downloading them.

---

### Post by Rocket2DMn on 2008-06-18
FYI:
```
connor@lappy686-mk2:~$ apt-cache depends mplayer
mplayer
  Depends: libaa1
  Depends: libamrnb3
  Depends: libamrwb3
  Depends: libartsc0
  Depends: libasound2
  Depends: libatk1.0-0
  Depends: libaudio2
  Depends: libaudiofile0
  Depends: libc6
  Depends: libcaca0
  Depends: libcairo2
  Depends: libcdparanoia0
  Depends: libcucul0
  Depends: libdbus-1-3
  Depends: libdbus-glib-1-2
  Depends: libdv4
  Depends: libdvdnav4
  Depends: libenca0
 |Depends: libesd-alsa0
  Depends: libesd0
  Depends: libfaac0
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libfribidi0
  Depends: libgcc1
  Depends: libggi2
  Depends: libgif4
 |Depends: libgl1-mesa-glx
  Depends: <libgl1>
    libgl1-mesa-glx
    libgl1-mesa-swx11
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libjack0
  Depends: libjpeg62
  Depends: liblame0
  Depends: liblircclient0
  Depends: liblzo2-2
  Depends: libmad0
  Depends: libmpcdec3
  Depends: libncurses5
  Depends: libogg0
  Depends: libopenal0a
  Depends: libpango1.0-0
  Depends: libpng12-0
  Depends: libpulse0
  Depends: libsdl1.2debian
  Depends: libsmbclient
  Depends: libspeex1
  Depends: libstdc++6
  Depends: libsvga1
    svgalib1-libggi2
  Depends: libtheora0
  Depends: libvorbis0a
  Depends: libx11-6
  Depends: libx264-57
  Depends: libxext6
  Depends: libxinerama1
  Depends: libxt6
  Depends: libxv1
  Depends: libxvidcore4
  Depends: libxvmc1
  Depends: libxxf86dga1
  Depends: libxxf86vm1
  Depends: mplayer-skins
  Depends: ttf-bitstream-vera
  Depends: ttf-dejavu
  Depends: zlib1g
  Suggests: ladspa-sdk
  Suggests: <libdvdcss>
  Suggests: mplayer-doc
  Suggests: w32codecs
  Conflicts: mplayer-nogui
  Replaces: mplayer-nogui

```
Those are all packages that mplayer depends on.  You may have many already, but it is indeed a lot like RomeReactor said.  You can use an alternate install cd as repository by popping it in the drive and running
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install mplayer
```
I'm not entirely sure that mplayer will be available on it though (it's in the multiverse repository, as well as the 3rd party Medibuntu repos).

---

### Post by RomeReactor on 2008-06-18
Not to mention that most of those dependencies *have dependencies of their own*; apt-rdepends mplayer gives this:

---

### Post by vivekrocks on 2008-06-18
Thanx a lot people, even I think that better to hav an internet connection on that system too. And I've checked my DVD which contains packages. It does not have multiverse componenet in pool :( . I need only x11 for now. Thats what it asks for, when i say configure! Ne way to get all the packages related to that? I hav installed whichever are there on the DVD

---

### Post by RomeReactor on 2008-06-18
You could take a look at the dependencies file in my previous post (download it and double-click on it to extract the text file); if you're on a windows machine at the moment, move the file to your Ubuntu system. Once there, look at the dependencies and search for them in Synaptic; take note of which ones are not installed and search for them [here]("http://packages.ubuntu.com/"). Please note that this is a very tedious process, and the best solution would be for you to connect your system to the internet--even for a short while-- and use Synaptic to get mplayer.

---

### Post by vivekrocks on 2008-06-18
THANX A LOT RomeReactor :)

---

