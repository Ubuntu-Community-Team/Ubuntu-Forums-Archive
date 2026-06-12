---
title: "No sound when playing media / Rhythmbox mp3 in Hardy"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by ian320 on 2008-05-08
Fired up rhythmbox today for the first time on hardy expecting things to go as easily as they did with 7.10, but I guess I was wrong. Before installing libxine1-plugins, like I did in Gutsy, I figured I would give Rhythmbox a try, because it suggested I install gstreamer0.10-plugins-ugly and gstreamer0.10-ffmpeg to get mp3's player. After doing that, they added fine to the library, but when I click to play them, nothing happens, the slider just stays all the way to the left.

So, I tried removing those two packages and installing libxine1-plugins, but then rhythmbox asked me to install the codecs again, which I did. Still nothing.

I also tried the advice listed [here]("http://www.ibeentoubuntu.com/2007/10/worried-about-how-to-play-mp3-and-divx.html") and [here]("http://ubuntuforums.org/showthread.php?t=755939"), to no avail.

Here is my current state:

[LIST]
[*]Firefox plays sound just fine
[*]VLC, Totem look like they are playing audio files, and for video files the video plays, but no sound can be heard.
[*]On Rhythmbox the slider stays all the way to the left when I click to play, and the music never starts. I also have to force quit rhythmbox because closing it on its own does not work.
[/LIST]
I may have gotten myself into quite the conundrum here, so I would appreciate any help.

---

### Post by ian320 on 2008-05-08
It is just as well that I get no reply, after a reboot everything seemed to work itself out. And that was one of the few things I enjoyed about linux, that it didn't have to go all windows on me and reboot with every update.

---

### Post by ojintoad on 2008-06-01
I had this error and found this thread, you may want to check out this bug report thread:

[https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/25750](https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/25750)

The post of interest is from Bernard Drapeau:

> 
Rythmbox "is playing but there is no sound".

I solved this problem in Hardy 8.04 alpha 3 i386 by specifying the ALSA driver. The could be a problem with hardware autodetection on your computer.

(Hardy is the only system working on my box. I cannot help you for Ubuntu 6.06.)

In Hardy alpha 6 i386, I left the settings to autodectetion and it works properly

In the menu you go to System / Preferences / Sound. Then change "Sound Events" to ALSA, and "Music and Movies" to ALSA

I followed the very last instruction and it resolved the problem without restart.  I am taking a guess and saying that a restart solves it by autodetecting the correct output device/system.

---

### Post by BearWayne on 2008-06-02
mp3 playback was working fine on my hardy installation. Until I discovered that it no longer worked. I guess mp3 playback was zapped by a recent update.  My sound configuration is set to "Auto Detect".  Rebooting resolved my problem as well.

---

### Post by MaindotC on 2008-06-22
Star for you, ojin.  I've run into this issue a lot - what is the point of including Pulse Audio in Hardy?  Does ANYONE use it and does it work???  Strange.

---

### Post by 449 on 2008-06-22
I'm having very similar issues.

---

### Post by Bennimal on 2008-08-25
@ Topic: Setting the automatic config off will help i guess. Every other program has sound here just my favorite player doesn't. All of a sudden since the last restart :(

@ Pulseaudio: On my Desktop I have two soundcards and pulseaudio is the best solution (and easiest) i found to handle that.

---

### Post by Crafty Kisses on 2008-08-25
Post the results of > lspci

---

### Post by audreymac on 2008-08-25
I have sound with Realplayer/Rhythmbox but I can't get sound playback from the sound recorder (trying to record with mic) which came as installed with Ubuntu8.04

---

### Post by dharmabruce on 2008-09-18
Following: 'System / Preferences / Sound. Then change "Sound Events" to ALSA, and "Music and Movies" to ALSA' resolved this problem for me without restart, as well.

---

