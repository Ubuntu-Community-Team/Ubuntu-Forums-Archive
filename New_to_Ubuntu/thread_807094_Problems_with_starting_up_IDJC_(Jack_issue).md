---
title: "Problems with starting up IDJC (Jack issue)"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by knokkels on 2008-05-25
Hi All, 

I am relatively new to Ubuntu, currently running Ubuntu Hardy Heron, which works pretty well I must say. 
Now for my problem:
I am an online dj, who would like to stream via a shoutcast application, so I ended up with IDJC. 
But it seems I can't seem to start it up due to Jack. 

I have posted some screenshots of my problem, and I hope somebody can help me.. As I would like to dj next thursday at the latest lol 
(Hopefully will have this sorted out before then. :)

[ATTACH]71576[/ATTACH]

[ATTACH]71577[/ATTACH]

[ATTACH]71578[/ATTACH]

[ATTACH]71579[/ATTACH]

Basically my problem is that I after installing IDJC I am getting error messages (see the images) 
Nomatter how I tinker with the settings, I also installed all the packages needed absolutely, and also the ALSA package except for 3 .. it still comes back with errors.

If anyone has any idea, that would be greatly appreciated. 

Tia 

Knokkels

---

### Post by markbuntu on 2008-05-25
From the first screen try changing your input and your output device from default to one of the options listed, try alsa first before the hardware options which are listed hw0:0, hw0:1 etc. If you have more than one sound card this is especially important.

Also get the alsa default sound cofiguration app with synaptic. I do not remember how it is listed but if you search alsa in synaptic you will find it. Install it and you will find it in System/Preferences and you can chose the default output for alsa. Then go to System/Preferences/Sound and change all the options from automatic to alsa. You should also get jack connect which you can use to configure and chain your jack connections.

I do not dj so I don't know how IDJC works but if it works through jack this might help.

I had a lot of trouble with jack and alsa but the above steps seemed to straighten it out at least on the sound card and being able to listen and capture end of things.

Let us know if this works.

---

### Post by knokkels on 2008-05-26
Hmmm I tried all of the above, thank you very much ..and yay it doesnt give any errors.. but still no sound, working on that.. thank you markbuntu, that helped me a lot

I can see that it is running though, and clicking icons (such as phone and mic does give static)

trying the input/output settings

---

### Post by knokkels on 2008-05-29
I got the sound working with the cooperation of a friend of mine, but I want to connect to a shoutcast server, and got a patch for it.. sound and all worked before the patch was installed .. and now basically back to square one, and still only ogg support :(

---

### Post by markbuntu on 2008-05-29
There are abunch of alsa plugins for pulseaudio and ogg and xmms and just about everything else. Get them and set your Sound to ALSA. Sometimes a patch will reconfigure everything to its own desires and screw up everything else so you have to reconfigure manually.

I use alsa as a default because it works for me and jack and ogg and pulseaudio and xmms2 apps will all go through alsa with the plugins and the right configurations. Some people have had success setting all their defaults to pulseaudio and ogg and using those plugins but I personally have not.

The thing here is that linux offers a zillion ways to use your sound and the more stuff you try to use the more complicated things get. Some apps are written for pulseaudio, some for ogg, some for xmms or xmms2 which is entirely different than xmms and not necessarily compatible. What you get is more choices and also more opportunities to confuse your sound setup and yourself.

I have been trying to get streamtuner to work with rythmbox for a few weeks now and have made "some" progress.It is an old xmms app and xmms has been replaced by xmms2 and as I said, they are not entirely compatible.  I can get it to use totem but that is not my goal. I can also get it to pop up a gtkxmms2 player but the streams will not play but anything in the player will. I saw someone get it to work with rythmbox once but then it crashed and wouldn't do it again, same with audacious. So, it is a combination learning experience and exploration.

Just fool around with stuff and you will eventually hit a combination that works for you and along the way learn a lot about how things work. That's what I do.

---

### Post by knokkels on 2008-06-02
hey there Mark ... well got it working by fiddling with stuff .. settings and all that ..
Not tried the plugins yet, will do soon enough ... I am getting A Connection To A Radio Server Failed now

So I thought maybe some instances of Jack or IDJC are failing, 

ps -aux | grep Jack
killed any and all instances

ps -aux |grep idjc
killed any and all instances

Tried again, still same msg .. rebooting doesnt help .. It sometimes just drops connection without previous warning ... I have the new IDJC with MP3 support which supports Shoutcast and thats been installed correctly. Anything I am missing here?

---

