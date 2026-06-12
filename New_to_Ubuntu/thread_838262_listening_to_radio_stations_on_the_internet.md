---
title: "listening to radio stations on the internet"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by bcvc on 2008-06-23
brand new user and semiliterate in computer usage.  All I want to do is to be able to listen to radio stations on the internet.  I downloaded realplayer, what do I do now?
thank you

---

### Post by unoodles on 2008-06-23
I would recommend using either Rhythmbox or Banshee, both have easy Internet Radio support

---

### Post by dracayr on 2008-06-23
you don't need realplayer. just open a player of your choice, there should be a corresponding Action in the file or file->open menu

dracayr

---

### Post by wolfen69 on 2008-06-23
first you should get the medibuntu repos.
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```then
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` 
you do not need realplayer for anything. this is what i do.
```
sudo apt-get remove totem-mozilla
```
```
sudo apt-get install mozilla-mplayer vlc
``` you should now be able to play anything.

---

### Post by hovzio on 2008-06-23
hi,

I think streamtuner is a real cool program. you can access shoutcast and many other stations. Theres a type plugin for it called streamripper (must be installed seperatley) to record the music. In most cases it will cut the songs seperatly while naming them appropriatley. Both programs should be  in the repos. (I know for gutsy they are.)

You will need a front end player like xmms or totem. You just choose a radio station in streamtuner and it will open it up in your player of choice.

VLC also lets you access shoutcast etc.

---

### Post by markbuntu on 2008-06-23
You can use tunapie with rythmbox, it has tons of stations.

If there is a particular station you want to listen to you can got to their web site and start the stream and then copy the url into the rythmbox new internet station box. Sometimes you have to try a their different streams to get one that works. Also smoe stations are using a new windows proprietary format that is usable only for windows. If you find one of these complain to the management.

I wish I could get streamtuner to work with rythmbox, but alas, is not possible.

---

### Post by TeoBigusGeekus on 2008-06-23
[http://ubuntuforums.org/showthread.php?t=793851]("http://ubuntuforums.org/showthread.php?t=793851")

---

### Post by cespinal on 2008-06-23
> **hovzio said:**
> hi,

I think streamtuner is a real cool program. you can access shoutcast and many other stations. Theres a type plugin for it called streamripper (must be installed seperatley) to record the music. In most cases it will cut the songs seperatly while naming them appropriatley. Both programs should be  in the repos. (I know for gutsy they are.)

You will need a front end player like xmms or totem. You just choose a radio station in streamtuner and it will open it up in your player of choice.

VLC also lets you access shoutcast etc.


Srsly??? If get to rip the music from my favorite internet radio player Im going to be the happiest man on earth!... good bye azureus!

---

