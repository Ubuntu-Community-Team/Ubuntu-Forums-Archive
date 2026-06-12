---
title: "[SOLVED] Having problems with installing codec to play mp3's in Songbird"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by sedea on 2008-10-19
I just purchased a new (larger and faster :P ) hard drive for my laptop, and I set up XP and Ubuntu on it as a dual boot, as I figured that I might be using Linux more in the future, based on the disappointment that was Vista. So my linux experience is all of 2 days.

Things have been going well so far; however, I've come across a bit of a weird problem when it comes to using Songbird.

After discovering that mp3 support was not native to Ubuntu, I went out to figure out how to get a codec to play all my files (I have no intention of converting ~160gb of music into ogg's... :P ).

I figured out that I needed to install the fluendo-mp3 codec thing for gstreamer, as this is apparently what Songbird uses? (I don't quite understand, but sure). So, I downloaded this, and extracted the codec, which ended up sitting on my desktop. I then tried to use the instructions I found here:

[http://blogs.sun.com/observatory/entry/playing_your_mp3s_with_songbird](http://blogs.sun.com/observatory/entry/playing_your_mp3s_with_songbird)

But seeing how the pfexec command apparently does nothing, and that there is in fact, no gstreamer-0.10 directory, under /lib, I was a little confused. So I did some exploring/googling.

I added the 'gstreamer extra plugins' that I found under the add/remove programs menu in Ubuntu (which apparently includes an mp3 codec for gstreamer). I also executed this command in the terminal:

[http://ubuntuforums.org/showthread.php?t=504379](http://ubuntuforums.org/showthread.php?t=504379)

At this point, I was able to play mp3s in Songbird, so I was happy, and I deleted the codec that I had initially extracted, that was sitting on my desktop. After I turned the computer off and on though, I was no longer able to play mp3s in Songbird.

I figured that maybe it was because I deleted the codec off my desktop, so I re-extracted it and put it back there... to no effect. So I removed the 'gstreamer extra plugins' application, and reinstalled it... to no effect. Then I re-ran that script in the above link... to no effect. 

Then I figured I'd move the codec off my desktop, directly into the /lib directory, even though there was no /gstreamer-0.10 directory within it, as there seemed to be a bunch of other .so files there (which I'm assuming were other codecs)... to no effect.

So I'm out of ideas at this point.

Anyone have any suggestions?

---

### Post by hansdown on 2008-10-20
Hi sedea.

Click on applications> add and remove.

Search for mp3, and add gsteamer extras.

---

### Post by t0p on 2008-10-20
The easiest way to enable mp3 playback is to install the package **ubuntu-restricted-extras**.  Open a terminal (**Applications > Accessories > Terminal**) and type:

```
sudo apt-get install ubuntu-restricted-extras
```

This will enable mp3 codec and many other proprietary codecs - plus java, flash... loads of fun stuff!

---

### Post by sedea on 2008-10-20
Tried both of those suggestions, with no improvement.

-gstreamer extras were already installed.

-Running that command in terminal yielded:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.

Which I'm assuming also validates that the app in question is already installed on my computer.

---

### Post by sedea on 2008-10-20
I tried uninstalling and then reinstalling both songbird and the 'gstreamer extra plugins' app (which includes the mp3 codec) today, but still no luck with mp3 playback in songbird. :(

---

### Post by hansdown on 2008-10-20
Hi sedea.

If you click on system> administration> synaptic package manager, then search for libdvdcss2. This should help.

---

### Post by sedea on 2008-10-20
I looked in the Synpatic package manager, but didn't find the libdvdcss2 package listed, so I googled it, and found this:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html)

I tried this first:

$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

*Then, add the GPG Key using the following commands*

$ sudo apt-get update

$ sudo apt-get install medibuntu-keyring

$ sudo apt-get update

But that didn't work for some reason... I couldn't figure out what the message in terminal was referring to exactly.

So I tried this instead:

$ sudo apt-get install w32codecs libdvdcss2

This did work, and libdvdcss2 is now showing up in synaptics package manager...

but...

songbird still will not play mp3s :(

---

### Post by sedea on 2008-10-20
Solved!!!

Via a problem that was completely unrelated to codecs. I have 3 partitions on the laptop - one for XP, one for Ubuntu, and one for all my files (music, videos, etc.)

As such, the partition will all my songs is not mounted or whatnot in Ubuntu by default apparently. So it was never a problem with codecs, it was simply that Songbird has no idea where the hell the file was that it was actually trying to play.

On that note, is there anyway to make it such that this partition is permanently available to Ubuntu, immediately upon startup?

---

### Post by kansasnoob on 2008-10-21
I like to use ntfsprogs but it allows access to ALL ntfs files, even the ones you shouldn't mess with.

Many people prefer nfts-config. They're both available in synaptic.

---

### Post by sedea on 2008-10-21
Works perfectly. Thanks!

---

