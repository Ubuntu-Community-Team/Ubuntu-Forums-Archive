---
title: "Tip: Realplayer mozilla plugin"
date: 2006-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by livingtarget on 2006-06-19
Just a little heads up,

**Description:**
[INDENT]
I experienced this problem that most media in firefox would play fine using the Mplayer plug-in. However with real player (*.rm/*.ram) files there would be a slight delay when using alsa (alsa mixing is rather important for me personally, so no OSS). This is annoying when you see people speak and then a few milliseconds later you hear the sound.

I couldn't even remember if real player came with a plugin by itself. Which of course it did. However I found mplayer plugin to override it by default. Type: "about:Plugins" in firefox title bar to find out.

So I went to /usr/lib/mozilla-firefox/plugins/ and removed "mplayerplug-in-rm.*". That is the plugin that exclusively handled real media.

Low and behold when visiting the BBC website for live world cup footbal it worked. I've now got alsa with smooth playback and it won't pause when switching screens.[/INDENT]

**Steps to take:**

1. Install Realplayer
[INDENT]> **sudo apt-get install realplayer**

or just follow this guide *(thank you Stubby)*:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29)
[/INDENT]

2. Remove/Rename mplayerplug-in-rm.* if you have it.
[INDENT]> **sudo rm /usr/lib/mozilla-firefox/plugins/mplayerplug-in-rm.***
[/INDENT]

3. Check the Realplayer Options in startmenu -> multimedia -> Realplayer 10 and then going in the menu to Tools -> Preferences
[INDENT]
-> If your screen flickers deselect "xvideo"
-> Use common sense with the buffering settings.
-> Read the following bit about turbo play!

**Turboplay**
Realplayer likes to buffer things but it will only buffer things based on the internet connection you set in it's preferences when "Turbo play" is enabled.

**Example:**
With turbo play enabled and setting you network speed to T1 (1.5mb/s) realplayer will decide with that kind of internet speed you never need to cache anything unless the stream goes faster then the speed of your T1 which is (1.5mb/s). This is alright if you are on a T1 because it will not be buffering a lot, but if your speed is a lot lower then that. Say you only have the capability to hit 512kb/s then it will just not be able to handle the amount of data in the stream.

**Solution:**
Disable turbo play -or- select your correct connection speed.
[img]http://www.ttr-dcli.org/~squad/realplayer.png[/img]
[/INDENT]

**Final Step:**
[INDENT]
Relaunch Firefox and watch world cup football :-\" (you may need to be located in the UK to see some/all clips).

See attached screenshot, how it looks when working.[/INDENT]

---

### Post by bionnaki on 2006-06-20
thanks...been trying to figure this out. did not mplayer to handle real media - thats what realplayer is for.

simply removing the mplayer real plugin worked like a charm.

---

### Post by stubby on 2006-06-21
Thanks for the guide. Just to clarify,

sudo apt-get install realplayer 

installs realplayer 8

sudo apt-get install realplay

installs realplayer 10 if you have the PLF repositories in your sources list. Thanks for the tip regarding the flicker issue.

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

---

### Post by traherom on 2006-06-21
It's very close to working. Unfortunately, things look like crap (somewhat minor problem, see screenshot. Partially due to adblock.) and (way more importantly) it only plays the first three seconds of the BBC stream.

Any thoughts?

---

### Post by stubby on 2006-06-21
[QUOTE=traherom]It's very close to working. Unfortunately, things look like crap (somewhat minor problem, see screenshot. Partially due to adblock.) and (way more importantly) it only plays the first three seconds of the BBC stream.

Any thoughts?[/QUOTE]

Did you deselect the xvideo thing?

---

### Post by livingtarget on 2006-06-21
[QUOTE=traherom]It's very close to working. Unfortunately, things look like crap (somewhat minor problem, see screenshot. Partially due to adblock.) and (way more importantly) it only plays the first three seconds of the BBC stream.

Any thoughts?[/QUOTE]

You can hide the adblock tabs by going in Tools -> Adblock -> Preferences and then click on the "Adblock Options" button and deselect "obj-tabs". Depends if you think of them as annoying or just helpful.

Realplayer likes to buffer things but it will only buffer things based on the internet connection you set in it's preferences when "Turbo play" is enabled. 

**Example:** 
With turbo play enabled and setting you network speed to T1 (1.5mb/s) realplayer will decide with that kind of internet speed you never need to cache anything unless the stream goes faster then the speed of your T1 which is (1.5mb/s). This is alright if you are on a T1 because it will not be buffering a lot, but if your speed is a lot lower then that. Say you only have the capability to hit 512kb/s then it will just not be able to handle the amount of data in the stream.

So disable turbo play -or- select your correct connection speed. (see: attachment)

I'll add this to the original post.

---

### Post by livingtarget on 2006-06-21
[QUOTE=traherom]It's very close to working. Unfortunately, things look like crap (somewhat minor problem, see screenshot. Partially due to adblock.) and (way more importantly) it only plays the first three seconds of the BBC stream.

Any thoughts?[/QUOTE]

Ah right, let me see. ](*,) Sorry to make a seperate post but i'd rather split this up with the previous post.

In the screenshot you posted it clearly says the clip is 3 seconds long (see: 0:00-0:03). I know this is confusing on the BBC side, that clip is just an intro clip. While looking at the same screenshot; to get the headlines, look in the right bottom corner and either click:

The news in three minutes
-or-
The latest full news bulletin

I fell for that too the first time :cool:

---

### Post by pkunal on 2006-06-22
OK the solution posted above is partially working. Example if you go to guide.real.com, the site will manage to open the RealPlayer.

But if you go to another site like say CBS News.com which hosts Video using *.rm file it will still bring up MPlayer (no video...what an annoyance)

OK the complete solution is on the MPlayer-PLugin's website:
You have to remove all mplayerplug-in-rm.* files whereever you find it in your system, as mentioned in this thread.
Additional steps are: From : [http://mplayerplug-in.sourceforge.net/config.php](http://mplayerplug-in.sourceforge.net/config.php)
Edit the mplayerplug-in.conf files (as many as you can find on your computer) and set enable-rm, enable-helix, enable-smil to '0'.
Also remember to delete  $HOME/.mozilla/pluginreg.dat 
Close Firefox & Mplayer
Restart Firefox, visit CBS News.com and check whether it now brings up RealPlayer for rm files.

Thanks,
pkunal

---

### Post by aev on 2006-07-05
[QUOTE=stubby]Thanks for the guide. Just to clarify,

sudo apt-get install realplayer 

installs realplayer 8

sudo apt-get install realplay

installs realplayer 10 if you have the PLF repositories in your sources list. Thanks for the tip regarding the flicker issue.

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Multimedia_Player_.28RealPlayer_10.29)[/QUOTE]


Thanks for the tip :D 
I dont like the BIN file for realplay. It places things everywhere. Then if you want to uninstall you have to look thru the intsall.log files - a waste of time.

---

### Post by beameup on 2006-07-07
You have to subscribe to the BBC site if you are an international user. I think adblock is blocking that text. See attached.

I haven't gotten it to work with CBS yet. Real pops up for a second in the video window and it goes white or it sits on loading 10%

---

### Post by ThrashJazzAssassin on 2006-07-12
To stop mplayer from playing real streams its a lot easier to right click on mplayer while its running, configure, and deselect real media. Now real player will take over.

---

### Post by SirPecanGum on 2006-09-30
What an effort! I have a similar problem with Totem apparently doing -trying to do - the job of Realplayer. There seems to be no plugin setting in Firefox as there is in Opera. I have used Opera to find out where all the codecs are but now, I just can't be bothered with it. Life is too short for this. I'm off to XP. No offence Ubuntu et al who enjoy this but I just want to use it, not play with it. I know it is only marginally better in Windows and then not necessarily but this codecs issue has just pushed me over the edge. When I can watch the BBC in any web browser let me know and I will return, wallet open.

---

