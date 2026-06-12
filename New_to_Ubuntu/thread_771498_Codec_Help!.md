---
title: "Codec Help!"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by kringle on 2008-04-27
In order to do the right thing, I guess, I purchased the Fluendo codec pack for my new install on of Hardy Heron.  However, after copying the files to /usr/lib/gstreamer, where there are a bunch of other files, I still can't play back .mp4, .avi, frankly any video file including DVD's.  I can listen to mp3 now and watch .wmv, but that's about it.  I've searched all over these forums and Googled it, but I can't find out what's going on.  When I try to play a DVD the codec buddy suggests I try to install the "ugly" set of plugins.  Doesn't that defeat the purpose of buying the Fluendo plugins? When I try to open a mp4 file, Totem states can't find location.

Help please!!

---

### Post by PhoenixP3K on 2008-04-27
Medibuntu might be what you need to fix all your problems

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After adding the repos according to the webpage, install the w32codecs using a terminal window or the Synactip Packet Manager.
The webpage also explains how to enable playing DVDs.

> sudo apt-get install w32codecs

---

### Post by mgmiller on 2008-04-27
OK, so you bought the codecs, now just install the ones that work and you can consider yourself paid up.

Go to System > Administration > Software Sources and make sure  the first 4 sources are checked.

Close the box and open a terminal by going to:
Applications > Accessories > terminal 
type the following and hit enter:
```
sudo apt-get update
```
then:
```
sudo apt-get install ubuntu-restricted-extras
```
(I am assuming you are running Ubuntu.  If you are running Kubuntu, change the command to kubuntu-restricted-extras)

That will get you java, flash, msttcorefonts and a lot of other things.

Now, for DVD's, type the following in the terminal and hit enter:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then do the same with this:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

What we have just done is added a new repository called "medibuntu" and it's gpg key.  This is the multimedia repository that contains proprietary codecs, like the ones you just paid for.

Now, let's install codecs to play DVD's:
```
sudo apt-get update
```
```
sudo apt-get libdvdcss2
```

And, just for good measure:
```
sudo apt-get install ffmpeg
```

This package contains the ffplay multimedia player, the ffserver streaming
server and the ffmpeg audio and video encoder. They support most existing
file formats (AVI, MPEG, OGG, Matroska, ASF...) and encoding formats (MPEG,
DivX, MPEG4, AC3, DV...).

And finally:
```
sudo apt-get install w32codecs
```

You should be pretty set now.

Have fun and welcome to Ubuntu.  :popcorn:

---

### Post by linmix on 2008-05-03
I forgot about the ffmpeg stuff, but even after following your suggestions to the letter* I can't seem to open certain .avi files. Totem tells me : could not determine type of stream. It's doing mp4 and other avi files OK

* *sudo apt-get libdvdcss2* should be *sudo apt-get **install** libdvdcss2*

BTW the .avi file I can't open is Xvid format

---

### Post by b_d on 2008-05-03
i am having the same problem. though i have some anime in .avi format that runs fine .. i cannot get any of my players to run my .avi movies. i am using vlc,kaffine,Mplayer,totem,xine. i even tried vlc in wine ...

iv done everything in this post and still no movie for me :(

---

### Post by linmix on 2008-05-06
Oh bother! Never mind, the file was corrupted. I found a backup I made some time ago and it worked flawlessly.

---

