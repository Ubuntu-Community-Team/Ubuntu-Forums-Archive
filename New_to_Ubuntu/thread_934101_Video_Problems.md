---
title: "Video Problems"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by alican timur on 2008-09-30
Well, i have a geforce 8800, and i'm trying to watch very neat hdtv videos. 
The thing is, i had mplayer, totem, kaffeine coming by default, and VLC as my own choice. i had installed vlc from the repositories, but the hdtv videos seemed to have very low quality when i tried to watch them in fullscreen view. now i know they seem better than this on a windows platform, so i thought there must be a problem, and uninstalled vlc from synaptic, and downloaded and compiled the source code. This one did the same thing, moreover when i try to watch .avi files on other media players, all the videos come with a green/purple hue.

It changed nothing, plus, I'm trying to uninstall all the media players and codecs etc. to install again cleanly, and i have a VLC media player i cannot erase. 

Help please?

---

### Post by aeiah on 2008-09-30
have you installed the restricted video driver for your card?

---

### Post by rybaxs on 2008-09-30
are u using Ubuntu 8.04? all players had a green/purple hue? try totem.. then go to edit->preferences->display to balance the color at hue

hope this thing works..

---

### Post by alican timur on 2008-09-30
yes i did. i installed the restricted drivers. can you help me uninstalling vlc first? i compiled & installed it and now can't find it's folder.

---

### Post by alican timur on 2008-09-30
it's not an issue of the color.. it's something to do with drivers/codecs. In windows it used to happen after the 6th vlc player window opened at the same time.

---

### Post by rybaxs on 2008-09-30
you've downloaded and compiled the source code? Applications -> Add/remove... try to uninstall there or delete it from source, or there is a problem on the file permissions.

---

### Post by alican timur on 2008-09-30
i can't find the source. where do you install by default when you make make install?

---

### Post by Dougie187 on 2008-09-30
the program is probably somewhere in /usr/bin or in /bin. but its not a good idea to just go in there and delete the program, because there are other files that the source creates for the program to use. Thats why it's only a good idea to compile from source if you really need to do it, like there is no other way or you need something specifically from that. It is not in any package manager if you intall from source.

The easiest way to remove a package you got from source is to get the source again, do your 
```
./configure
```
and then type
```
sudo make clean
```
and you can try
```
sudo make uninstall
```
Or something like that. it depends on the program and the make file what flags remove it so you might have to dig through the makefile to fine the appropriate flag to type, but one of them should remove it from your computer.

---

### Post by 3rdalbum on 2008-09-30
As for your "green/purple" video problem, this has been around in Nvidia's drivers since forever... *sigh*.  "Oh yeah, we fixed the colours problem in our new drivers".  "Yeah, you fixed it for my card, but now lots of people are complaining that their cards are giving them the wrong colours in videos!"

You can work around the problem by changing the video output module. All non-Gnome video players have different video output modules that you can select in the preferences. Nvidia only breaks one or two of them at a time, so you can use the ones that still work.

For Gnome-based media players, you go into gconf-editor and go to the following key:

/system/gstreamer/0.10/default/videosink

When you click on "videosink", the description field tells you what the other choices are.

Or, you could disable the Nvidia driver and just work with the 2D accleration, which has never given me any video problems. The less-extreme route is to upgrade the drivers to the newest version, if possible, as Nvidia has probably temporarily shifted the video problem to another series of cards in the new driver.

You can tell I don't like Nvidia, right? :-D

---

