---
title: "Windows Media player classic"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Beatbreaker on 2008-06-08
Hi, i'm writing this because i've tried almost every media player that Ubuntu has to offer and i still can't find anything i like 

To name a few:

I've tried Totem and for some reason it plays media at slow motion
I've tried Kaffeine but it crashes when i search through movies
I've tried VLC but I don't like it's layout, full screen mode has no controls in it, and i can't control anything with my mouse in it (apart from full screen).
I'm pretty sure i tried XINE too but that didn't work out either.

I loved Windows Media Player Classic. It looked like a piece of crap, no fancy stuff on it but it could play everything under the sun. I could stop, start, control volume and full screen with my mouse

Is there anything in Ubuntu that comes anywhere close to that?

[IMG]http://img511.imageshack.us/img511/5251/wmpccv3.jpg[/IMG]

---

### Post by avtolle on 2008-06-08
I believe in VLC you need to install a plugin to allow control via a mouse (other than the full screen selection). Under Settings>>Preferences, in the left window there is a selection for Interfaces. Take a look at that (expand the list) and see if there isn't something there that may help you.

---

### Post by balachandarlinks on 2008-06-08
Installing Codecs

    Open a terminal and type :

    sudo -s -H  or  sudo -i

    and then enter your user password.

    After that :

      apt-get update

      apt-get upgrade

    To be upgraded. Please check that you have all repositories enabled in Software sources.

    Then these commands :

    apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse 

    gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg     libdvdread3

    Now you have the most of the codecs needed to play most of multimedia you may own. 
 


       Now all ur players will work fine....

---

### Post by Beatbreaker on 2008-06-08
> **avtolle said:**
> I believe in VLC you need to install a plugin to allow control via a mouse (other than the full screen selection). Under Settings>>Preferences, in the left window there is a selection for Interfaces. Take a look at that (expand the list) and see if there isn't something there that may help you.

I've checked that out, There's a "mouse gestures" section in the "control interfaces" part of preferences. It does nothing when i click on it though.  i read on the VLC forums that it would be working in the Nightly Updates version 0.9.xx but it still didn't change anything - and it's even more annoying because i've got split control window and movie windows.

do other people get at least some controls when in full screen mode?

---

### Post by Beatbreaker on 2008-06-08
> **balachandarlinks said:**
> Installing Codecs

    Then these commands :

    apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse 

    gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg     libdvdread3


all of those commands did something but not this last one - the top half did but there looks like there's something missing from the bottom half

..or should that be all one line?

---

### Post by avtolle on 2008-06-08
That should have been all one line. To get these additional codecs, etc., at the terminal```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg  libbdvdread3
```

---

### Post by Beatbreaker on 2008-06-08
Thanks for your help avtolle but no changes made

> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


the default "media player" and gstreamer are still playing AVIs and other media like in slow motion.

---

### Post by balachandarlinks on 2008-06-08
For me after installing this totem plays all medias fine......
  Do u have good amount of ram ,..i have 1 GB......:KS

---

### Post by Beatbreaker on 2008-06-08
I've got a gig, i'm pretty sure it's DDR2 running at a pretty fast speed

VLC plays the videos at the proper speed, i just can't stand the layout - when i go to full screen mode i don't have any controls, and can't control anything with my mouse.

---

### Post by halln on 2008-06-08
> **Beatbreaker said:**
> I've got a gig, i'm pretty sure it's DDR2 running at a pretty fast speed

VLC plays the videos at the proper speed, i just can't stand the layout - when i go to full screen mode i don't have any controls, and can't control anything with my mouse.

have you tried mplayer at all mate? I think this is the one you like.

---

### Post by AnRa on 2008-06-08
You may try [GNOME MPlayer](apt:gnome-mplayer).

---

### Post by Beatbreaker on 2008-06-08
> **AnRa said:**
> You may try [GNOME MPlayer](apt:gnome-mplayer).

That was an awesome way to get me to install it!

unfortunately it works like the default "media player" but worse. It's really slow for only a few seconds then the movie section of the window goes black.

---

### Post by forger on 2008-06-08
looks like you need w32codecs or w64codecs:
[www.medibuntu.org](www.medibuntu.org)
here's some other codecs i have on my ubuntu:
```
sudo apt-get install --reinstall lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3
```

you should really stick to mplayer - or try smplayer which has simpler interface. but i use mplayer or totem player for my everyday use (movies, dvd etc)

---

### Post by macness on 2008-06-08
or as suggested before there's also mplayer.
```

sudo apt-get install mplayer
```

---

### Post by cariboo on 2008-06-08
If you don't like the way vlc looks you can change the skin to one that suits you.

Jim

---

### Post by 3rdalbum on 2008-06-08
If you right-click when VLC is in full-screen mode, you get full controls in a popup menu.

You could also try [Gxine]("apt:gxine"), which has an option for controls when you're in full-screen mode.

The other option is to get an infrared remote control and reciever that is compatible with Linux. That way you can use any media player.

---

### Post by marine63 on 2008-06-08
yeah i agree wmpc rocks

---

### Post by cozmicharlie on 2008-06-08
This may help you [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Beatbreaker on 2008-06-08
I've tried just about all of those suggestions - I have NO idea as to why but in those programs they play VERY slowly, stop and then crash the player. What is going on here? Can i just uninstall everything to do with those programs, reinstall them and will it be ok? It's honestly sending me crazy. To top that off now Amrock refuses to work and i've lost my system tray diplay of programs. I'm not entierly impressed at the moment. 



cariboo907 - I've tried different skins with VLC, it still won't allow for mouse gestures. And i don't like the skins because i can't drag them around my Compiz Fusion cube.

---

### Post by cozmicharlie on 2008-06-08
> **Beatbreaker said:**
> I've tried just about all of those suggestions - I have NO idea as to why but in those programs they play VERY slowly, stop and then crash the player. What is going on here? Can i just uninstall everything to do with those programs, reinstall them and will it be ok? It's honestly sending me crazy. To top that off now Amrock refuses to work and i've lost my system tray diplay of programs. I'm not entierly impressed at the moment. 



cariboo907 - I've tried different skins with VLC, it still won't allow for mouse gestures. And i don't like the skins because i can't drag them around my Compiz Fusion cube.


It may be easier to start over with a fresh install.  But before you  do, try this first and see if it helps.  Open vlc - in the menu go to settings>preferences>output modules.  Check the advanced button on the bottom.  It should be using default - change these and see if one of these other settings gives you better quality video.  Try X11 first then work your way down. 

I think the main objective is to get your music and video running with the native programs then once you know the music and video are working you can add packages to see which you prefer.  I think now you may have added and removed so many packages it is screwing up your system so a fresh install my be best at this point.

I also use MPC in Windows and I really like it but I have found that mplayer (with the smplayer front end) and vlc work great and I can do anything with these packages I could do with MPC.  Ogle is very good for playing DVD's (it allows you to use the menus).  I don't use Amarok though a lot of people like it.  There are a number of good music managers/players that may suit your needs.  I would recommend if you start with a fresh install that you start by installing the various codecs (video and audio) first - then add the packages once you have the video and audio working.  It is actually even easier than the post I referred to above.  If you do a fresh install - post back here before you add anything and I can walk you through the entire process.

---

### Post by sdowney717 on 2008-06-08
smplayer and VLC for me
I can play iso video files with VLC
And I can view video when running compiz with VLC by switching the video output. It needs to be x11. found under output modules

---

### Post by Beatbreaker on 2008-06-14
I haven't touched Ubuntu since last week due to the frustration that it gave me, but i gave it another shot lastnight. THe videos work well in every player - I do prefer totem above anything else after trying them out .

Anyway some time this morning they've slowed down again, maybe they'll get better with a restart but i wanted to show everyone what my termianal is saying about it to see if there is a reason why this stuffs up

[http://pastebin.com/f7b7a7842](http://pastebin.com/f7b7a7842)

what's going on there? Untitled.avi was working perfectly before.

---

### Post by Beatbreaker on 2008-06-16
bump

---

### Post by imon9 on 2008-06-16
use smplayer
[http://smplayer.sourceforge.net/images/screenshots/smplayer_gnome.jpg](http://smplayer.sourceforge.net/images/screenshots/smplayer_gnome.jpg)

download it from synaptic :) or go to their website
[http://smplayer.sourceforge.net](http://smplayer.sourceforge.net)

u wont regret it

---

### Post by Nepherte on 2008-06-16
I recently dumped SMPlayer for Gnome MPlayer, both front-ends for MPlayer. It has much less features accessible by the gui. Simplicity is the keyword for that front-end, which is why I like it so much. Configuration can be done by other means if you really want to anyways. Gnome Mplayer is in the repositories.

---

