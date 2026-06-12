---
title: "Skype sound output PulseAudio"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by economy on 2008-11-08
hey all,

I'm running 8.04 and I'm trying to get skype to work. when I log in, it plays the very beginning of the log-in sound, but when I try to make a test sound or call, it will not make any sound. the microphone works fine, and the video is flawless from my webcam, but I can't seem to get the program to make a sound.

Any ideas?

---

### Post by Mark_in_Hollywood on 2008-11-08
Try this:

Open a terminal. At the prompt type:

alsamixer

using the keyboard arrow keys, move the volume up and down.

Open skype, check the Options/Sound devices. Select hardware devices. Try the test call again. If it works, close the terminal. (not necessary but un-clutters the screen)

I just installed skype last week and it's making me nuts. I have to open the terminal every other time I use skype. It's not quite a bug, and nothing to report, and I'm hoping the coders are aware of it.

---

### Post by economy on 2008-11-09
I tried that, still nothing. I'm not sure why this is happening, before I reinstalled Ubuntu it worked perfectly, but this time around I can't get the sound output. 

If I can't figure out a way to get Skype to use the damn laptop speakers, can anyone recommend a service that would allow me to VOIP with Skype users?

---

### Post by Crafty Kisses on 2008-11-09
Open Skype, then do the following **Options ---> Sound Devices**, once you've done that choose your sound device and it should work.

---

### Post by economy on 2008-11-09
codename, thanks for that, but i've crossed that bridge twice already.

i have installed pulseaudio and set it up to be the device used in any situation, and the only program that will not accept it is skype. if i revert back to the other options or "default device", still nothing. there's some other problem, unless my pulseaudio setup was incorrect. that's my question, not how to use skype from the configuration menu...

---

### Post by Mark_in_Hollywood on 2008-11-12
DISCLAIMER: I don't know PulseAudio.

Uninstall Skype

sudo aptitude remove skype

reboot or wait until you re-power up

sudo aptitude install skype

---

