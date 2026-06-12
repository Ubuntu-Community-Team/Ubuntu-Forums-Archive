---
title: "need some help wih streaming realplayer video &amp; audio in firefox"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by dpjpmp on 2008-11-08
Hi all! I have a problem with streaming realplayer streams in Firefox. I am using Ubuntu 8.04 and a fresh install at that. I followed the directions on a "sticky" post here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I did option 1 (Gecko Media Player), not option 2. All media seems to work fine but real streams. It looks like it tries then just stops or sits there.

I looked in Firefox file associations and it has Reaplayer 8 associated with the real files it looks like. Also, on the web pages themselves, it looks like it is opening in Gnome Player? (In Windows at the moment)

Anyway, if you all could help me with this, I sure would appreciate it as this is my first bump.

Here are the web pages that I am going to when testing realplayer streams:

Audio: [http://oneplace.com/ministries/Turning_Point/](http://oneplace.com/ministries/Turning_Point/)

Video: [http://www.pbs.org/wgbh/nova/darpa/program.html](http://www.pbs.org/wgbh/nova/darpa/program.html)

I wil be away for the day, but will check in when I get back, so if I don't answer right away, please be patient.

---

### Post by FreewheelinFrank on 2008-11-08
I've found the MPlayer Mozilla plug-in the most reliable way to play Realplayer streams.

The Audio from the site you linked to played in Flash, with Flash utilising the Mplayer plug-in, seemingly.
The video from the site you linked played in the Mplayer plug-in.

---

### Post by gandaran on 2008-11-08
the best player to handle real video and audio are mplayer and all mplayer clones like gecko and smplayer.
for any of these player to work with firefox you need to install the same player plugin for firefox and just one plugin, you have to remove or disable the totem plugin or the other plugin won't work.
mplayer and clones require you install the w32codecs package from medibuntu repo [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by FreewheelinFrank on 2008-11-08
Just checked out the gnome-mplayer gecko-mediaplayer plugins and they work too- and have nicer menu bars!

---

### Post by FreewheelinFrank on 2008-11-08
Oops! Spoke too soon. No video. 

EDIT: Or audio for Realplayer.

Other formats seem to work.

The mozilla-mplayer plug-in may be the one to choose if you want to play Realplayer content.

---

### Post by dpjpmp on 2008-11-08
Thanks. Now, do I need to remove my gnome-mplayer gecko-mediaplayer plugins and then install mozilla-mplayer plug-in? From what I have read, to many plug-ins will confuse Firefox. And (Hem,Hem) just what is the process to do this? (Kind of new to Ubuntu and all the sudo stuff) Maybe just install media connectivity extension in Firefox and direct it?

---

### Post by FreewheelinFrank on 2008-11-09
I can't tell you if removing gnome-mplayer and gecko-mediaplayer and installing mozilla-mplayer and mplayer will get Realplayer streams playing because I haven't tried, but that set-up was working for me previously. I never watch or listen to Realplayer streams now the BBC has dropped that format- so I'll stick with gecko-mediaplayer for a while and see how it goes.

You need to go to System>Administration>Synaptic Package Manager.

Use the search feature to look for gnome-mplayer and gecko-mediaplayer: right click and select 'Mark for complete removal'. Click 'Apply'.

Search again for mozilla-mplayer and mplayer, right click and select 'Mark for installation'. Click 'Apply'.

---

### Post by dpjpmp on 2008-11-09
Thanks FreewillinFrank! I think that I am going to do like you are doing; stick with what is already installed. If I find that I need to stream a realplayer file in Firefox, I'll consider changing. I'm sure you noticed that the urls that I posted also offered Windows Media Player options and they work fine. Frankly, the Gecko setup us just so smooth on my system that I don't want to change it. 

Oh, by the way, love the user name!:lolflag:

---

