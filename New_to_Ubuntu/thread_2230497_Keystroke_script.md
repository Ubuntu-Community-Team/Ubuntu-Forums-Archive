---
title: "Keystroke script?"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by bug67 on 2014-06-19
Can someone that knows how to do such things help me out?  I need a script that I can launch on demand that triggers a keystroke or simulates mouse movement once every 3 or 4 minutes.  The reason I need such a thing is because I want to inhibit the screensaver.  I used to use caffeine for such things but, as of the last few versions, it has become unusable.

I've seen some things that seem similar to what I want but, they don't seem quite there.

I'm assuming that I would just need to double click the script file to launch it?  How would I then go about shutting said script down?

See, even though I've been using various 'buntus for quite some time, my skill set is not up to the task of doing these sort of things for myself.  I would appreciate some assistance.  Thanks in advance.

---

### Post by ajgreeny on 2014-06-19
I presume if you want to just inhibit screensaver starting up, not stop it totally, that you want this just a certain times, eg when running a video player or similar.

You could do this simply with a compound command for the video player that first stops the screensaver, then starts the player, and finally when the player closes, the screensaver is restarted. This will depend on the screensaver you are using, of course, but in my xscreensaver setup it might be
```
killall xscreensaver && vlc && xscreensaver -no-splash
```

You might be right that it can be done in a different way with simulated mouse moves or keystrokes, but I am thinking on the fly here, and I admit I have never tried this myself.

Some video players will automatically stop gnome-screensaver, I believe, but I'm not sure about xscreensaver.

---

### Post by bug67 on 2014-06-19
That might do it.  :-k

Here's my situation and why I want this.  I'm on Xubuntu 14.04 using Xscreensaver on a dual monitor setup.  I have things set up to start Xscreensaver after 10 minutes of inactivity then, the machine goes into sleep mode 30 minutes after that.

I use this machine for an audio entertainment system a lot!  I run Clementine and like to have its visualizer (projectM) running full screen.  However, I have to continuously provide user input (every 9 minutes or so via a mouse wiggle) to keep things from going to screensaver and, eventually, sleep.  Not the most efficient use of my time when I just want to have music playing in the background while I do other stuff around the house.

It's be nice to have a script or an app I could just "launch" that would keep the screen from blanking on demand.  Caffeine used to do just that.  No longer.  And the dev is not hearing any suggestions of changing it back to its once useful state.

I could just go into settings and disable the screensaver and sleep functions from there but, man, that's an awful lot of clicking around.

---

