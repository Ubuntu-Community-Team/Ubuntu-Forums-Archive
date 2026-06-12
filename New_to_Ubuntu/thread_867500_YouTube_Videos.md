---
title: "YouTube Videos"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-22
God, this is so ******* annoying. YouTube videos rarely work for me, I gotta reload them a couple times, if i'm lucky, or like 20 times for them just to start. 

It's not my internet connection, because i got a 5mbit service. I'm pretty sure I have all the essential things for the videos to run properly, because they run fine once i get them started.

---

### Post by cozmicharlie on 2008-07-22
Provide a little more info and lets start the trouble shooting process.
What Ubuntu are you using (Hardy, Gutsy)?  It sounds like you may have a conflict with different plug ins.
[LIST=1]
[*]I assume you are using Firefox but what plug in have you set up (mplayer, vlc other)?
[*]What specifically happens?  Do they just not play.  Do they start playing then stop?  Do they just keep buffering.
[*]Have you enabled the Medibuntu repository?
[*]Have you installed the gstreamer plug ins, ffmpeg, libdvdread3, w32 codecs, libdvdcss2, libdvdnav, Ubuntu restricted extras?
[/LIST]

This is a good source to look through [https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3](https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3)

This is imho the best How To on multimedia and has sections for trouble shooting [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Take a look at those sources but don't hesitate to post back if you are not sure how to do something.

---

### Post by adobrakic on 2008-07-23
I'm running the heron, and yeah i'm using firefox w/ mplayer plugin. What specifically happens is that I get that little loading icon in the middle of the video, and it just stays. Yeah, I've enabled the medibuntu respository, and i'm pretty sure i've installed all those plugins, but i'll make sure.

---

### Post by mali2297 on 2008-07-23
Do you have **flashplugin-nonfree** installed? (Not mozilla-plugin-gnash or swfdec-mozilla.)

---

### Post by cozmicharlie on 2008-07-23
> **mali2297 said:**
> Do you have **flashplugin-nonfree** installed? (Not mozilla-plugin-gnash or swfdec-mozilla.)

This is a good suggestion.  Use this command when installing the flashplugin-nonfree.

```
sudo apt-get purge flashplugin-nonfree gnash gnash-common libflash-mozplugin libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

This will take care of any conflicts.

---

### Post by tuxxy on 2008-07-23
check your browser plugins for 

Shockwave Flash

File name: npwrapper.libflashplayer.so

If you cant see it then you need to install flashplugin-nonfree and the browser plugin

---

### Post by Sealbhach on 2008-07-23
> **cozmicharlie said:**
> 

This is imho the best How To on multimedia and has sections for trouble shooting [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


+1 to that. That guide is superb.



.

---

### Post by ice60 on 2008-07-23
if you can't find a solution there are scripts about that let you use a different player, i thought i saw some on this site, but can't see any right now -
[http://userstyles.org/](http://userstyles.org/)
[http://userstyles.org/styles/search/youtube](http://userstyles.org/styles/search/youtube)

i found this
[http://webscripts.softpedia.com/script/Multimedia/Video/MPlayer-Youtube-Video-Streamer-32816.html](http://webscripts.softpedia.com/script/Multimedia/Video/MPlayer-Youtube-Video-Streamer-32816.html)

here's another that uses VLC and greasemonkey
[http://netsharc.wordpress.com/2007/03/31/youtube-via-vlc/](http://netsharc.wordpress.com/2007/03/31/youtube-via-vlc/)
EDIT, that link ends up linking to this url -
[http://netsharc.wordpress.com/2008/02/15/youtube-via-vlc-3rd-attempt/](http://netsharc.wordpress.com/2008/02/15/youtube-via-vlc-3rd-attempt/)

you might need to do some searching, but there are ways to stream youtube videos if you can't get flash working.

there are loads of great scripts, i have download links, lots of video size choices and even better quality video formats to pick from on youtube by using different scripts 8)

---

### Post by RequinB4 on 2008-07-23
Totem has a youtube plugin that allows you to search and watch in realtime any youtube video.

---

