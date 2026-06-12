---
title: "how to  play mp4 in ubuntu 9.04"
date: 2009-05-29
forum: Philippine Team
---

### Post by cloud69 on 2009-05-29
I was wondering if anyone knows how to play mp4 video in ubuntu. It plays on my laptop but the video is out of sync from the audio. I use mplayer found it on the other forums. thanks.

---

### Post by loell on 2009-05-29
try installing libdvdcss2 from medibuntu


```

sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get install libdvdcss2


```

---

### Post by cloud69 on 2009-05-29
> **loell said:**
> try installing libdvdcss2 from medibuntu


```

sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get install libdvdcss2


```

ok i'll try this when i get home. thanks.

---

### Post by loell on 2009-05-29
np. :)

---

### Post by Samhain13 on 2009-05-30
Try VLC. :D

---

### Post by pinoyskull on 2009-05-30
> **Samhain13 said:**
> Try VLC. :D
+1 for VLC

---

### Post by tagabukid on 2009-05-31
kung out of sync ang audio and video sa mplayer you can use the + and - keys to try and resync them as you play.. in 100 ms intervals. goodluck! :-)

---

### Post by jsgotangco on 2009-05-31
yeah that should also work if you are playing your video with subtitles.

---

### Post by Nhatz on 2009-06-02
Yeah VLC rules!!! hahahha :D

ASTIG!!! :guitar:

---

### Post by dannybuntu on 2009-06-04
+1 ulit VLC :)

Eto popcorn 
:popcorn:

---

### Post by leipogs23 on 2009-06-04
How bout 3gp and wmv files?

---

### Post by Samhain13 on 2009-06-04
^ VLC will be able to handle those too.

---

### Post by leipogs23 on 2009-06-04
> **Samhain13 said:**
> ^ VLC will be able to handle those too.

Wow. Ayaw kasi sa Totem.hehehe. Pano ko install VLC without internet access??? San ko sya madodownload? Ala ako makita e. Thanks

---

### Post by Samhain13 on 2009-06-04
^ [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Kailangan mo nga lang talaga ng Internet access. Di ko lang alam kung may puwede kang i-download na .deb package for offline installation. Google mo na lang.

---

### Post by leipogs23 on 2009-06-04
> **Samhain13 said:**
> ^ [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

Kailangan mo nga lang talaga ng Internet access. Di ko lang alam kung may puwede kang i-download na .deb package for offline installation. Google mo na lang.

Puro google na nga lang po ginawa ko dito sa office e. Ala ako makita na offline installation or .deb package. i'll post it pag nakita ko.

---

### Post by Script Warlock on 2009-06-05
internet dependent talaga ang ubuntu di pwede install wala inet di to parehas sa M$ bsta may cd installer oks na. aabot din tayo dyan

---

### Post by leipogs23 on 2009-06-05
> **Script Warlock said:**
> internet dependent talaga ang ubuntu di pwede install wala inet di to parehas sa M$ bsta may cd installer oks na. aabot din tayo dyan

Got one sir from getdeb site. What I mean sir is installing without the use of apt-get.hehehe

---

### Post by Script Warlock on 2009-06-05
> **leipogs23 said:**
> Got one sir from getdeb site. What I mean sir is installing without the use of apt-get.hehehe

ganun pa rin pag may kailangan na component ang ininstall mo internet din ang tinatakbuhan ni ubuntu...

---

### Post by vinutux on 2009-06-05
install Vlc

or

mplayer

or 

xine

---

### Post by Samhain13 on 2009-06-05
> **leipogs23 said:**
> Got one sir from getdeb site. What I mean sir is installing without the use of apt-get.hehehe

Kung makakuha ka ng .deb, it works just like an installer.exe file. Ang gagawin mo lang ay right-click the .deb and "Install with GDebi Package Installer". ;)

Kung gusto mo ng command line:
```
$ sudo dpkg -i pangalan_ng.deb
```

(Wag lang siya maghahanap ng iba pang files sa Internet, pero sa tingin ko hindi naman na.)

---

### Post by vinutux on 2009-06-05
if u want only 3gp wmv intstall realplayer 

install deb from here [COLOR="Red"][www.real.com/linux]("www.real.com/linux")[/COLOR]

---

### Post by leipogs23 on 2009-06-05
> **vinutux said:**
> if u want only 3gp wmv intstall realplayer 

install deb from here [COLOR="Red"][www.real.com/linux]("www.real.com/linux")[/COLOR]

Thanks. I'll try this out

---

### Post by Rasheeke on 2010-01-23
What about karmic?  I get absolutely no sound or video when trying to play an mp4 in avi.

---

### Post by Ravskie on 2010-01-25
install gnome alsa mixer might work for you

---

