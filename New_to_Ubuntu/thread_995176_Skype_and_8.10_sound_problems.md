---
title: "Skype and 8.10 sound problems"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by figi22 on 2008-11-27
I just installed Skype on 8.10 but am having problems testing out the sound.   Does anyone know what the settings in Skype options - sound devices - should be?   It's a Dell Studio laptop, brand new Intel Core2Duo.   Integrated webcam seems to be working OK.

It did look from the Skype website that 8.10 is not supported... but I'd already installed the operating system by that point.

---

### Post by mikewhatever on 2008-11-27
Here are mine, works fine. What exactly is the problem?

---

### Post by figi22 on 2008-11-27
Hmm.. I tried your settings but same problem.

I can hear the test call, but I can't hear my voice in playback.   I just tried testing the mic using the Sound Recorder and that didn't work either - that must be the problem.   Not sure how to fix it though.

---

### Post by mikewhatever on 2008-11-27
Test all other options for sound out, one of them might work.

---

### Post by doyouhas on 2008-11-27
I get a similar problem. My audio works perfectly until I turn my USB web cam on and then the sound quality goes down the toilet. I turn off the web cam, it works fine again. Any help here?

---

### Post by figi22 on 2008-11-27
It's not quite the same.

I have an integrated webcam.   The video part is working OK, and the sound output is working fine.  It's just that the sound input (microphone) is not working.    The Dell Studio has left and right digital array microphones on the display next to the webcam, and also an analogue mic.   Neither appear to be working.

I've tried turning sound settings on and off, but I'm not sure what I'm supposed to be using.   At the moment then it's on HDA Intel (Alsa Mixer) and recording settings of Front Mic Mixer, Capture, etc. are all unmuted.  The toggle switches are all off.

Can anybody tell me what Sound Preference settings and general Sound settings they use?

---

### Post by clinkletter on 2009-02-21
you might also consider 
[http://justmyself.wordpress.com/2008/12/07/audio-probelm-of-skype-in-ubuntu-810/](http://justmyself.wordpress.com/2008/12/07/audio-probelm-of-skype-in-ubuntu-810/)

I just tried and it worked fine.  Looks like there may be some kind of a problem with pulse.

Carl L.

---

### Post by josil on 2009-02-22
I had the same problem. I consider the instructions from [http://justmyself.wordpress.com/2008...in-ubuntu-810/](http://justmyself.wordpress.com/2008...in-ubuntu-810/)

********************
Solution 2 (Worked for me )
Go to Application -> Accessories -> Terminal, write following commands one by one
Close Skype
sudo kill pulseaudio
sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio
now start Skype and everything is perfect.
*********************************
Worked fine. My final settings are:

---

