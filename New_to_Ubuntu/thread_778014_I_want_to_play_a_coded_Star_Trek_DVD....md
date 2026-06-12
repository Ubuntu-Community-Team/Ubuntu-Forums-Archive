---
title: "I want to play a coded Star Trek DVD..."
date: 2008-05-01
forum: New to Ubuntu
---

### Post by mac9416 on 2008-05-01
Hello!

I want to watch Star Trek the Original Series on my Ultimate Edition machine (which I am proud to announce has a spankin' new DVD drive in it!) and I think I need to download some kind of media de-coders. I am at a Windoze computer and will probably download whatever I need with No NetDebs.
Thanks!

-mac

---

### Post by spacefreak86 on 2008-05-01
Um, okay? Try downloading the VLC media player, that tends to play almost anything. Otherwise, if you don't have internet connection, I suppose Windows Media Player or PowerDVD that I believe comes with Vista will play the DVD. You should be able to just pop it in and have it run, as it would with the medibuntu repositories installed on Ubuntu.

---

### Post by iSplicer on 2008-05-01
> **spacefreak86 said:**
> Um, okay? Try downloading the VLC media player, that tends to play almost anything. Otherwise, if you don't have internet connection, I suppose Windows Media Player or PowerDVD that I believe comes with Vista will play the DVD. You should be able to just pop it in and have it run, as it would with the medibuntu repositories installed on Ubuntu.

To do that, just run this in your terminal:

```
sudo apt-get install vlc
```

---

### Post by mac9416 on 2008-05-01
Well, the only trouble is that she ain't got the internet cap'n!
I have tried to play it in VLC, but it didn't work. I assume that the software it needs is on the internet.
And as far as WMP goes, I don't have Windoze on that particular computer. I like to stay away from that Microsoft stuff anyway.

---

### Post by lwvmobile on 2008-05-01
Hmmm... You might try VLC, it has DVD decryption support. How to get it from a Windows machine to your Ubuntu Machine is another story. Live long and prosper.

---

### Post by mac9416 on 2008-05-01
"I can do neither, for I have lost my internet connection, and my friend."

A misquote from "Amok Time".:)
Off-topic but funny.

---

### Post by iSplicer on 2008-05-01
> **mac9416 said:**
> Well, the only trouble is that she ain't got the internet cap'n!
I have tried to play it in VLC, but it didn't work. I assume that the software it needs is on the internet.
And as far as WMP goes, I don't have Windoze on that particular computer. I like to stay away from that Microsoft stuff anyway.

If you have a USB drive or a spare blank CD you can download the source from:

[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

and compile it on your main machine.

Good Luck

---

### Post by mac9416 on 2008-05-01
Thanks, i, but I've already got VLC. I will upgrade it, however, and see what I get.

---

### Post by iSplicer on 2008-05-01
While you are at it, have a read of this link, my friend:

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

It kinda sucks that you do not have access to the net, but in Linux, when theres a will, theres a way!

---

### Post by mac9416 on 2008-05-01
Man, oh man, that appears to be exactly what I needed. I'll use NoNetDebs to download that package, slip it onto a flash drive, install it on my main computer, and tell ya'll what comes of it.
Live long and prosper ya'll!
PS: Thanks, i! ;)

---

### Post by phread59 on 2008-05-01
Mac I'm a gonna go out on a limb here some.  I tried the vlc player thing back when I used 7.10, didn't work straight up.  I had to add 2 programs.  They are libdvdcss2 and w32codecs.  How you are gonna get them in without internet I do not know.  I got it in by :

sudo gedit/etc/apt/sources.list
and adding this at the bottom

deb http:[www.debian-multimedia.org](www.debian-multimedia.org) etch main
deb-src http:[www.debian-multimedia.org](www.debian-multimedia.org) etch main
then closed and saved and ran

sudo apt-get update 
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs

I also added the restricted files in synaptic.  I now am good to go.  I hope you get it fixed Grasshopper.

Mark Shuman

---

### Post by iSplicer on 2008-05-01
> **phread59 said:**
> Mac I'm a gonna go out on a limb here some.  I tried the vlc player thing back when I used 7.10, didn't work straight up.  I had to add 2 programs.  They are libdvdcss2 and w32codecs.  How you are gonna get them in without internet I do not know.  I got it in by :

sudo gedit/etc/apt/sources.list
and adding this at the bottom

deb http:[www.debian-multimedia.org](www.debian-multimedia.org) etch main
deb-src http:[www.debian-multimedia.org](www.debian-multimedia.org) etch main
then closed and saved and ran

sudo apt-get update 
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs

I also added the restricted files in synaptic.  I now am good to go.  I hope you get it fixed Grasshopper.

Mark Shuman


Yepp. If you absolutely hate VLC, thats the method to use in order to get your DVD's working globally on your system.

---

### Post by mac9416 on 2008-05-01
Thanks guys. I gotta run so I can't D/L the second file mentioned. I'll get it later.

---

