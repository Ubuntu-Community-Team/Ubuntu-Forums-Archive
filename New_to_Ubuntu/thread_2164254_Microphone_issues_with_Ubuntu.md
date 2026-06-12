---
title: "Microphone issues with Ubuntu"
date: 2013-07-30
forum: New to Ubuntu
---

### Post by ludvig-almvang on 2013-07-30
Hi! I am having some issues with my microphone. It works with great quality on windows, but with Ubuntu it sounds kind of sparkly when I talk.
This is something my friends on skype want me to fix, they say it sounds annoying so please help me.
I am running on Ubuntu 12.04 64-bit and my microphone is the one inside my Steelseries Siberia v2

- I have tried mixing with the settings in PulseAudio but I could not find anything that helped
- I have tried using other softwares than skype to check that skype wasn't the problem

---

### Post by JeQhdMD on 2013-07-30
Here's a similar thread:  [URL="http://ubuntuforums.org/showthread.php?t=2160756&highlight=skype+settings"]http://ubuntuforums.org/showthread.php?t=2160756&highlight=skype+settings
[/URL]
Also, here is a detailed sound troubleshooting guide for Ubuntu:   

[https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting)

---

### Post by ludvig-almvang on 2013-07-31
Thank you for your reply :)

But, the thread you linked me is not related to my problem. He has problem with skype sounds, I have problem with my mic in Ubuntu.
And the troubleshooting did not help either :(

---

### Post by Ubunterrific on 2013-07-31
I actually remember coming across this a year or two back. (Skype's a nightmare in every respect #Tox)

The way the crackling stopped was done like so:

edit /etc/pulse/default.pa 

e.g.  ```
sudo gedit /etc/pulse/default.pa
```

and look for the line:
```
load-module module-udev-detect
```

add "tsched=0" to the end of it, so it looks like:

```
load-module module-udev-detect tsched=0
```

And then i think logging off and back on again (just to restart the pulseaudio server) should have the new code up and running - and with no skype crackling. Annoying that this is still an issue, but that's skype for ya!

---

### Post by SweetAurora on 2013-07-31
Maybe your mic is set too high in ALSA?

In a terminal, type "alsamixer" and use the left and right arrow keys to navigate. Look for sliders that have "mic" in them. Use the up and down arrows to adjust their volume. tinker around a bit with the slider(s) untill the static stops, but you are still audible. Also, when on a slider, push "m" on the keyboard to toggle mute on or off. When you are done, hit the "esc key" to exit alsamixer.

---

### Post by Ubunterrific on 2013-07-31
> **ludvig-almvang said:**
> Thank you for your reply :)

But, the thread you linked me is not related to my problem. He has problem with skype sounds, I have problem with my mic in Ubuntu.
And the troubleshooting did not help either :(


Doy...i really need to go to bed, i totally misread your message. Well that should solve your friend's problem XD

I'm not really sure how we would solve your mic problem? From the looks of it, a few people have had your same issue on multiple operating systems and didn't offer a simple fix for it :/  I would recommend tweaking the 'mic' and 'mic boost' volumes a bit in:

```
alsamixer
```

in a terminal. (Press escape to quit it)   Sorry i can't be of more help.

---

