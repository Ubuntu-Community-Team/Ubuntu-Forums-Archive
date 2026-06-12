---
title: "Edgy Howto: Fix &quot;no sound&quot; problems when using Firefox and others at the same time"
date: 2006-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by bilange on 2006-11-19
This is a quick howto reguarding the problem some of you may have encountered when using Firefox on Edgy where the sound seem to not play, especially when using Flash videos. 

I assume this problem happens only/often on machines with low end soundcards, as it happened to me. For the record, I have an ATI Mobility chipset (on a laptop) which provides the soundcard. If this mini howto did help you, for curiosity's sake (and to help locate where the problem lies), please add a reply specifying what kind of soundcard you have.

--

**NOT PATIENT?** Heres the raw details (skip this paragraph if you want an in-depth explaination): In gnome-sound-properties, change the sound engine to ALSA; Install the package alsa-oss; Edit */etc/firefox/firefoxrc* so the variable FIREFOX_DSP equals to "aoss"; restart firefox and enjoy. (You may have to run firefox once with "aoss firefox" in a console, as I needed to do.)

-- 

DETAILED EXPLAINATION:

One thing I noticed is that Ubuntu is less severe reguarding playback in general when you change your sound engine to ALSA. In other words, I had *lots* of problems reguarding sound not playing back if I had two or more programs using sounds opened. Changing my sound "engine" (or whatever its called) to ALSA helped me play back sounds in general, except for Firefox where the flash player always wanted the soundcard all for itself. 

[indent][color=blue] To change your "sound engine", go to System, Preferences, Sounds (or type *gnome-sound-properties* in a console). If I remember correctly the default setting is autodetect for almost everything, change all the options to "ALSA - Advanced Linux Sound Architecture", and close the window. (You could always test it if you want ;))[/color][/indent]

As far as Flash is concerned, it seems that it does use OSS to output its sounds, and there is little we can do about this. There is no option inside Firefox to configure what sound engine to use, and neither does the Flash player. Fortunately there is a package available which "translates" or redirect anything going thru OSS towards ALSA, and thats how we'll control how Flash will use the sounds. Download the package alsa-oss.

[indent][color=blue] In a console, type in *sudo apt-get install alsa-oss*[/color][/indent]

The next step is where the actual magic happens. I found a website where it said to edit /etc/firefox/firefoxrc, and to change the FIREFOX_DSP line to *FIREFOX_DSP=&#8221;aoss&#8221;*. At this point you would need to restart Firefox (dont forget to note/bookmark this page!) and test if the sound from Flash can coexist with, say, Rhythmbox. 

[indent][color=blue] Open up a console and type sudo gedit /etc/firefox/firefoxrc. Modify the FIREFOX_DSP line so aoss is written in brackets. Save and exit.[/color][/indent]

However, when I did this for the first time it didnt work at all (nothing changed, the same "bug" was there), but I was able to make it work by forcing Firefox to use aoss to forward OSS thru ALSA (see below). I had to do that once then close Firefox, and then it would work completly (with the workaround, uh, working :)). Maybe your computer would need a reboot, maybe there's an old firefox process still pending preventing to make it work, I don't know (I didnt check at the time). If Firefox never want to correctly playback sounds unless you're calling Firefox with "aoss" in a console, you could also create a new shortcut calling "aoss firefox", at worst.

[indent][color=blue] To force Firefox to use alsa-oss, in a console type in "*aoss firefox &*", and test with a Flash movie if you can playback from multiple audio sources (multiple programs).[/color][/indent]

[indent][color=blue] You wouldn't need to call "aoss firefox" because we made that change in the firefoxrc file earlier, but if its the only way you can use the sounds correctly, create a new desktop shortcut and point it to "aoss firefox".[/color][/indent]

[indent][color=blue] If you are moderately confortable at manipulating files (in superuser/root mode) in a console, you can always try to install Flash 9 Beta (which helps fixing this issue) by downloading it [here](http://labs.adobe.com/downloads/flashplayer9.html). Read the readme file, they give you instructions about where to put this library file.[/color][/indent]


----

Thats it, that was my howto. If it was somewhat difficult to read/follow, bear with me. This is my very first Ubuntu howto ;)

If there's something that didnt make sense, dont hesitate to leave a message in this thread - english isnt my native tongue so I assume I made mistakes. If you have other useful infos about this bug/issue, feel free to comment below too - chances are that I might add them in the this post too (while citing sources/credits ;)

Sources: 
[indent]-[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)
-Vardyr and craigevil on #firefox (irc.mozilla.org)[/indent]

Thanks for reading! :)
-Bilange

---

### Post by mdecler2 on 2006-11-22
Great Howto! I could not get flash sound [in Firefox] to work in Dapper, but alsa-oss solved this problem. It seems correct that Firefox does steal the sound device for itself, I haven't been able to get that to work yet.
Thank you for the help!

---

