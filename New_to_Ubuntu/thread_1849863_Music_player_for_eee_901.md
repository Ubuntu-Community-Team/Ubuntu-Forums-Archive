---
title: "Music player for eee 901"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by t00farg0ne on 2011-09-25
Hi

I've just recently decided to install ubuntu 11.04 on my asus eee 901. Loving it so far but i'm trying to find the best solution for the main purpose of the netbook is as a music player through my old hifi.

So I'm looking for a media player software that can do the following:

-will work well on the eee 901
-will access the external hdd attached to my asus rt-n56u router vis usb (banshee does this)
- has an interface that will work ok on the small screen (banshee not so good here)
-can recognise id tags created on dbpoweramp rips (banshee does not do this)  
-Is easy enough to install, or has good instructions, i got lost trying to install 

any recommendations would be great.

thanks

---

### Post by linuxfreak003 on 2011-09-25
I don't know if they would work for everything you want specifically but you could try exaile(my music player of choice), amarok, xmms, or audacious(similar to winamp), there is also songbird or rythmbox. VLC is also very good. If you're looking for something with an easily accesible music library(kind of like iTunes) then you would probably want to use exaile, amarok, songbird, or rythmbox. VLC usually supports just about everything though.. I don't know which if any would work but those are some you can try play around with at least.

**Most of them can be installed pretty easily using apt-get install.

---

### Post by ajgreeny on 2011-09-25
I would suggest audacious as it is very low on resource requirements.  It's the music player in Lubuntu 11.04, and I think often overlooked in other ubuntu family members as well.

Alternatively you could look at mpd (music player daemon) plus a front end client such as pympd, but that will take a little more setting up than a local player.

---

### Post by BeRoot ReBoot on 2011-09-25
Seconding the recommendation for mpd, with ncmpcpp as the client.

---

### Post by pkg9991 on 2011-09-25
Rhythm box comes pre-installed for Oneiric
other wise you can get them from Ubuntu software center

---

### Post by candtalan on 2011-09-25
I was told that unity2d package installs and runs well in the 901. I have one and tried it - worth considering. In Ubuntu Software Centre.

---

### Post by t00farg0ne on 2011-09-27
thanks

I've gone with exaile and that seems to do the job quite well, only downside is maybe the look of it but definitely for now this is the best by far.

---

### Post by Paqman on 2011-09-27
> **t00farg0ne said:**
> 
-will work well on the eee 901

Rhythmbox runs fine on Eee PCs, I've got two.
> 
-will access the external hdd attached to my asus rt-n56u router vis usb (banshee does this)

If you set this up to be mounted automatically through /etc/fstab then every app on your system will be able to see it as if it's a local drive.

---

### Post by linuxfreak003 on 2011-09-28
Yeah I decided to go with exaile mainly because it's one of the easiest and you can have your whole music library there(mine is pretty big), It also seems to be fairly good at not crashing at random..

---

