---
title: "ipod alternate?"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by jmax123 on 2013-06-29
There are many threads on how to get an ipod to talk to ubuntu ... but none that I can find on alternates to iPod in Australia. I tunes in ubuntu is of course hopeless in ubuntu but what other portable media players work? An android device perhaps? An android device with a 32 gig flash drive you just
load video and music onto? Does ubuntu recognise android os's?. Can't seem to find out. Samsung have an android media player ... what player does work, that is fairly available in Oz, just plug and play without any crazy mucking about with itunes on ubuntu?

john

---

### Post by papibe on 2013-06-29
Hi jmax123. Welcome to the forums ):P

A few thoughts:

Some iPods work well in Ubuntu/Linux, specially the old ones. You don't use iTunes to sync music to them, though. When they work, they usually work fine with either Rhythmbox or Banshee.

Having said that, it is not a perfect solution. Sometimes they stop working, and the only solution is to reset them to factory settings using iTunes. Unfortunately, that means installing the latest firmware, and that may mean they won't work in Linux anymore.

There are well known mp3 players that work well with Ubuntu, e.g., Sandisk and iRiver. However, IMHO any phone, tablet, or player that can be mount as **mass storage device** should work fine.

Here's something you might find usefull:

[iPods and MP3 players in Linux]("http://www.youtube.com/watch?v=Y7SgEivcxl8&t=45m27s") (a video segment of an episode of the Linux Action Show). Here are the details  [notes]("http://www.jupiterbroadcasting.com/19307/cinnamon-desktop-review-las-s21e08/") from that video (look for Matt's Howto).

Hope it helps.
Regards.

---

### Post by 3rdalbum on 2013-06-30
> **jmax123 said:**
> Samsung have an android media player ... what player does work, that is fairly available in Oz, just plug and play without any crazy mucking about with itunes on ubuntu?

I've always used Sony Walkman MP3 players. They've been drag 'n' drop since 2007 (they mount as a USB Mass Storage device on Ubuntu, and as MTP on Windows).

You could certainly go with an Android device as they also work with drag 'n' drop, but be aware that Android 4.0 and above will only mount on Ubuntu 13.04 and above. Android 2.x-based devices will work as USB Mass Storage on any operating system.

---

### Post by kabukiM0n0 on 2013-06-30
I got myself a 4th gen ipod shuffle yesterday and out of the box it wouldn't recognize it (I used to use a 2nd gen shuffle no problem) Reading through a few threads I started to play around and now it mounts no problem on Gtkpod ... and my version is not even labeled under the options.  

As said it's kind of a hit and miss - if it does miss ... play around with it until it works.

---

### Post by newb85 on 2013-06-30
+1 to everything 3rdalbum said. 

I've used phones with Android 1.x and 4.x, and both have worked flawlessly drag-and-drop. 

I also have an old Walkman mp3 player. It also works great, with the caveat that the ID3 tags have to be the right version for the player to recognize them. It isn't equipped for version 2.x.

---

### Post by 3rdalbum on 2013-06-30
> **newb85 said:**
> +1 to everything 3rdalbum said. 

I've used phones with Android 1.x and 4.x, and both have worked flawlessly drag-and-drop. 

I also have an old Walkman mp3 player. It also works great, with the caveat that the ID3 tags have to be the right version for the player to recognize them. It isn't equipped for version 2.x.

My X-series doesn't seem to have any problems with ID3 tags. I assume ID3v2 is supported on newer players.

I don't know if this has been sorted out in newer players, but the Walkmans used to be very picky with what video formats they supported. You can encode for Walkmans in Handbrake if you know the settings, or I wrote a script called Blacklight that can convert videos to one of the correct formats. If you buy a Walkman and have any problems with encoding videos, send me a message and I'll give you the script.

---

### Post by newb85 on 2013-06-30
> **3rdalbum said:**
> My X-series doesn't seem to have any problems with ID3 tags. I assume ID3v2 is supported on newer players.

I would assume so, too.  As I said, it's an *old* Walkman...

---

