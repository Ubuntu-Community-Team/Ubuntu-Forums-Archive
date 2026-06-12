---
title: "How To: convert *.ape, Mac's lossless audio"
date: 2006-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by ex00r on 2006-04-15
Hi every body. This is my first post. I hope it's useful for you since i had a long time before i got my ape-files converted.

There you go:

**First** of all you need the (really good) audio-convert script.

Here you can download it: [http://freshmeat.net/projects/audio-convert/](http://freshmeat.net/projects/audio-convert/)

Here is the Post: [http://ubuntuforums.org/showthread.php?t=82806&highlight=ape](http://ubuntuforums.org/showthread.php?t=82806&highlight=ape)

```
sudo dpkg -i audio-convert_0.3.1.1-0ubuntu1_all.deb
```

you run the script like this:

```
audio-convert /*/your.file/
```

The script supports nearly every codec. WAV, Ogg, MP3, MPC, FLAC, APE, AAC, and WMA files. But the problem is, you normally haven't got the maclib's installed. So you have to get'm, here:

[http://prdownloads.sourceforge.net/mac-port/mac-3.99-u4-b3.tar.gz?download](http://prdownloads.sourceforge.net/mac-port/mac-3.99-u4-b3.tar.gz?download)

You have to compile those for your self.

```
tar zxvf mac-3.99-u4-b3.tar.gz
```

attention: you need those packages:
```
sudo apt-get install nasm
sudo apt-get install libgtk+2.0
sudo apt-get install libglib2.0-dev
```

then in your new folder:

```
./configure
```
```
make
```
```
make install
```

Basically this should be enough. You now can convert your ape files!


If you want to install the gstream monkey codec, it is here:

[http://rarewares.org/debian/packages/unstable/](http://rarewares.org/debian/packages/unstable/)

-> Download these three deb-packages and install them as always (dpkg -i):

- gstreamer0.8-monkeysaudio_0.8.2-0rarewares1_i386.deb
- libmac-dev_3.99+update4+build4-0.0_i386.deb
- libmac2_3.99+update4+build4-0.0_i386.deb

Another tip: If you want to get your xmms or bmp be able to play ape-files you could try out these sources (and compile them afterwords):

Here: [http://prdownloads.sourceforge.net/mac-port/](http://prdownloads.sourceforge.net/mac-port/)

For XMMS: xmms-mac-0.3.1.tar.gz
For BMP: bmp-mac-0.1.1.tar.gz

Have fun!

---

### Post by adamkane on 2006-04-23
There is an easier way to get full support for audio-convert. See Post 61 here:
[http://www.ubuntuforums.org/showthread.php?t=82806](http://www.ubuntuforums.org/showthread.php?t=82806)

---

