---
title: "The best music player in your opinion?"
date: 2012-02-04
forum: Recurring Discussions
---

### Post by dagroves on 2012-02-04
What is the best music player out there in your opinion?
I am using the default one on Ubuntu 11.10, Banshee. I am mostly looking for something that I can use with the sound menu like Banshee uses. Anything else?

---

### Post by johnnybgoode83 on 2012-02-04
I posted this on the other thread so I may as well post it here too :p

Clementine is easily the best music manager on Linux in my opinion and Guayadeque is the second best.

My only gripe with Clementine is a small one, it can't copy album art to my iPod. It's not a deal breaker though as I never browse by album art anyway.

---

### Post by dagroves on 2012-02-04
Just installed Clementine, so far, I am really liking it, I have already removed Banshee!

---

### Post by Bucky Ball on 2012-02-04
The answer to your question would depend on what you require from the music player. ;)

---

### Post by haqking on 2012-02-04
clementine...or if you like resource friendly then deadbeef

---

### Post by Version Dependency on 2012-02-04
Clementine is pretty sweet.

---

### Post by Rodney9 on 2012-02-04
> **version dependency said:**
> clementine is pretty sweet.

+1

---

### Post by TeamRocket1233c on 2012-02-04
Windows and Mac: iTunes.
Linux and BSD: VLC.

---

### Post by Linuxratty on 2012-02-04
> **dagroves said:**
> Just installed Clementine, so far, I am really liking it, I have already removed Banshee!

How? Neither Synaptic or the software center can find it.

---

### Post by Baldrick_NZ on 2012-02-05
I've used both Clementine and more lately Guayadeque, and I settled on the latter because it does more and seems lighter.

The thing I didn't like about Clementine was the way filing options (File, Edit, View, etc..) didn't show up in the Global Menu after a while. Meaning to actually turn it off, I had to right click on the launcher icon and quit that way.

---

### Post by bholten on 2012-02-05
I use Rhythmbox on my desktop and Sonata + MPD on my netbook because it uses significantly less resources.

---

### Post by nothingspecial on 2012-02-05
*Thread moved to **Recurring Discussions**.*

---

### Post by rudihawk on 2012-02-05
Rhythmbox for me lately. :)

---

### Post by grobar87 on 2012-02-05
MPD + Ncmpcpp

---

### Post by SeijiSensei on 2012-02-05
> **Linuxratty said:**
> How? Neither Synaptic or the software center can find it.

[http://www.clementine-player.org/downloads](http://www.clementine-player.org/downloads)

I can't for the life of me understand why clementine is not in an official repository, but you can add a PPA for it like this:

```
sudo add-apt-repository ppa:me-davidsansome/clementine
sudo apt-get update
sudo apt-get install clementine

```

Kubuntu developers -- please add clementine to the official repos.

---

### Post by Version Dependency on 2012-02-05
Clementine is in the software center in 12.04.  I'm pretty sure it was in 11.10 too.

---

### Post by rudihawk on 2012-02-05
> **Version Dependency said:**
> Clementine is in the software center in 12.04.  I'm pretty sure it was in 11.10 too.

I'm using 11.10 and it is in the repos!

---

### Post by Welly Wu on 2012-02-05
I like Clementine although I still use Banshee to rip CDs and convert them to .FLAC loss less audio files.

---

### Post by SeijiSensei on 2012-02-05
In KDE, you don't need a special program to convert to FLAC, Ogg, or MP3 if you have the codecs installed.  When you insert a music CD into a machine running KDE, it opens as a set of folders each representing one of the available codecs.  To rip a track you just drag it out of the appropriate folder.  There are also folders that provide access to the entire CD as a single file.

---

### Post by dagroves on 2012-02-05
> **Linuxratty said:**
> How? Neither Synaptic or the software center can find it.

If you are using 11.10 it is in the Repo's, just 
```

sudo apt-get install clementine

```

---

### Post by Hylas de Niall on 2012-02-05
I like Audacious.
I can't be doing with all the cataloging and stuff a lot of others have. I know where my music is stored and what i have on the drive, and i prefer to just point my player at a file or folder and hit 'play'.
:)

---

### Post by eltama on 2012-02-09
+1 Guayadeque.

Just don't install the version from the repositories, use this:
```
sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque-svn
```

---

### Post by wolfen69 on 2012-02-09
> **Version Dependency said:**
> Clementine is pretty sweet.
It sure is, but for *my* needs, vlc does just fine. I absolutely love listening to music, but I'm not an "audiophile" or picky. As long as it plays my music, I'm happy.

---

### Post by screaminj3sus on 2012-02-11
> **Baldrick_NZ said:**
> I've used both Clementine and more lately Guayadeque, and I settled on the latter because it does more and seems lighter.

The thing I didn't like about Clementine was the way filing options (File, Edit, View, etc..) didn't show up in the Global Menu after a while. Meaning to actually turn it off, I had to right click on the launcher icon and quit that way.

This is a known unity issue, and the latest clementine release works around this by disabling global menu support completely.

Personally I love clementine the most :) Haven't tried Guayadeque though.

---

### Post by Erik1984 on 2012-02-11
Rhythmbox seems to be the best overall for my needs.

---

### Post by Sylos on 2012-02-11
> **eltama said:**
> +1 Guayadeque.

Just don't install the version from the repositories, use this:
```
sudo add-apt-repository ppa:anonbeat/guayadeque
sudo apt-get update
sudo apt-get install guayadeque-svn
```

Another +1.

Handles large libraries well and has a nice interface.

I'll also throw one in for Aqualung for those people who want a 'jack aware' player so you dont have to switch jack off and engage the dreaded pulseaudio if you want to take a break from your audio work.

Cheers

---

### Post by screaminj3sus on 2012-02-11
Another one I am liking as of late is audacious. Never liked it much before, but in the latest version they added library watching and search and its pretty great. Really simple and functional.

---

