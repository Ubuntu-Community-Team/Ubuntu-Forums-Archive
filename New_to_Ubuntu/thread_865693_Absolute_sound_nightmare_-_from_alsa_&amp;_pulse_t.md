---
title: "Absolute sound nightmare - from alsa &amp; pulse to OSS and back"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by fogelfink on 2008-07-20
I seriously need help with my sound setup!
I have been using Ubuntu for 3 months and still cannot get my sound working properly.

I tried ALSA in combination with pulseaudio - i followed this thread for setting it up: [http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+solution](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+solution).  Initially that seemed to do the trick.  I have an external soundcard through which I wanted to channel the soundoutput from amarok, which worked for a while, but then amarok (set to use the pulse output plugin) crashed the system. 

So i looked for an alternative to pulse and began installing OSS version 4, following these instructions:  [http://ubuntuforums.org/showthread.php?t=780961&highlight=oss](http://ubuntuforums.org/showthread.php?t=780961&highlight=oss) .
That didn't solve my problems, but made them worse!  Though OSS started and I could play sounds on my internal soundcard, the usb soundcard (despite showing up in the OSSmixer) wouldn't play any sound.
After rebooting, OSS failed me completely - in the System/Preferences/Sound tab I couln't choose OSS as a sound device and couldn't define a Default Mixer.

Back to ALSA I thought, but then I couln't uninstall OSS!!! Synaptic wouldn't let me, so I followed these uninstall instructions: [http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054), without following the reinstall instructions of that thread.  Now I am still new to linux, but to me, what I did was not properly uninstall OSS, but remove references to OSS from the synaptic config file. Anyway,...

So then I wanted to go back to ALSA  and  yet again  followed  the steps of my first setup.(howto [http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+solution](http://ubuntuforums.org/showthread.php?t=789578&highlight=sound+solution) ). Now nothing works anymore. In the sound preferences, I get an error message for any sound device (ALSA, ESD and pulse) of missing audiosink - OSS still has not reapeared as an option  and no  mixer available.  Trying to use the pulse audio applet gives a connection failed error message.

So I am left with no sound at all and not a clue of what to do.

I would really appreciate if someone could tell me how to get a clean install of whatever sound setup.  All I want to do is play sound through an external soundcard (when connected, otherwise use the internal speakers) and I don't care if it's ALSA, pulse, or OSS, as long as they work.
I have spend the last three months struggeling constantly with my operating system, instead of actually using it and begin to think that that's what you do  in linux.

please heeeeeeeeeeeeeeeelllllllllllllllllllppppppppp.

---

### Post by Narqulie on 2008-09-24
Bump, I'm also suffering from somewhat the same probs :( Especially the last part:

> Now nothing works anymore. In the sound preferences, I get an error message for any sound device (ALSA, ESD and pulse) of missing audiosink - OSS still has not reapeared as an option and no mixer available. Trying to use the pulse audio applet gives a connection failed error message.

Pls to hlep kkkk :(

---

### Post by kansasnoob on 2008-09-24
This guide has worked quite well for me:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

It is possible that you might need to reinstall pulseaudio before beginning.

---

