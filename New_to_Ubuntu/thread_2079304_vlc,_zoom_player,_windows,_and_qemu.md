---
title: "vlc, zoom player, windows, and qemu"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by 9ine on 2012-11-01
Hello

I was wondering if anyone could help with this.

I have been enjoying using the very adaptable vlc player that Ubuntu offers but it does not work with some - not all just some - of my .m2ts files. Other players I have installed (MPlayer, Kaffeine, Movie Player) seem to be even further away from working with these files.

On my Windows set-up I have the excellent and without a doubt best player out there... Zoom Player. But its geared for Windows and is not available for linux. I have managed to to get it to load using Wine but it won't play *any* files at all from what I can tell.

My thoughts are now turning to the emulator qemu but I must confess I am having difficulty understanding any of the guides I have happened on. I am running Ubuntu 12.04 so what is it I need to do next? Is qemu available through Ubuntu Software Centre and therefore its just a case of installing it like any other software on there? Or are we talking something completely different altogether. For example, is qemu something you even install *into* Ubuntu?

Would appreciate any guidance, thanks.

---

### Post by GreatDanton on 2012-11-01
If you type qemu into search bar of Ubuntu software center you will see a bunch of applications there. I don't know which one you need, but yeah it's in there so you can install it like any other application.

---

### Post by qyot27 on 2012-11-01
In all seriousness, MPEG-2 TS is just one of those troublesome containers for FOSS applications at the moment.  Zoom Player was probably using a DirectShow-based playback filter (hence why it wouldn't work in Wine; Wine doesn't support DirectShow) that has nothing to do with the TS-handling abilities of libavformat.

Your best bet is to install mkvtoolnix and mkvtoolnix-gui and use that to mux the streams into MKV.  After that, it should work with pretty much all of those players you had issues with.

---

### Post by 9ine on 2012-11-01
Thanks for those replies. Will the muxing cause a deterioration in the final product/reduction in quality compared with pre-mux?

I see mkvtoolnix is available from the Software Center but where is mkvtoolnix-gui?

---

### Post by qyot27 on 2012-11-01
> **9ine said:**
> Thanks for those replies. Will the muxing cause a deterioration in the final product/reduction in quality compared with pre-mux?
All muxing does is change the container.  It doesn't touch the video or audio at all.  Although with a media player's better support for a container, you can get better playback.

> I see mkvtoolnix is available from the Software Center but where is mkvtoolnix-gui?
It might get installed with it.  I'm not sure of how Software Center displays this stuff.  All else fails you can use the [project's own repositories](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu) for Ubuntu, since it has newer versions (the Ubuntu repos have 5.1.0, whereas the newest version is 5.8.0).  

From the instructions on the mkvtoolnix site (the Terminal way given for ease of display):
```
wget -O - http://www.bunkus.org/gpg-pub-moritzbunkus.txt | sudo apt-key add -
sudo add-apt-repository "deb http://www.bunkus.org/ubuntu/precise/ ./"
sudo apt-get update
sudo apt-get install mkvtoolnix mkvtoolnix-gui
```

---

