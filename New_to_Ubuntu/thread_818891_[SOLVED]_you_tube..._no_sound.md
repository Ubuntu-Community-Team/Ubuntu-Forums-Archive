---
title: "[SOLVED] you tube... no sound"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by no1cares on 2008-06-04
speakers work and here sound when i play music from computer.....
I went to youtube and it said mozilla needs new software to watch this video or whatever. (the bar at top that appears when u need something to view a webpage).. it messed up somehow, cant explain how, i was doing other things while it was going and it just messed up... the video works but no sound.... 

need to know how to re-install the new software to watch the video. i know that is the problem.....

---

### Post by iaculallad on 2008-06-04
Try to install the libflashsupport:

```
sudo apt-get install libflashsupport
```

---

### Post by no1cares on 2008-06-04
tried it.
sudo apt-get install libflashsupport
 still doesent work.... would it be easier to just re-install mozilla???

---

### Post by no1cares on 2008-06-04
tried it.
sudo apt-get install libflashsupport
 still doesent work.... would it be easier to just re-install mozilla???

---

### Post by iaculallad on 2008-06-04
Try re-installing firefox:

But be sure to backup first your bookmarks and other data related to your profile.

```
$ cd ~/.mozilla
$ tar -cMf firefox.tar firefox/
```

---

### Post by Toshibawarrior on 2008-06-04
If none of that doesn't work just check the YouTube player's volume...set it to the max and be VERY SURE to have ALL soundcard dependent programs closed. i.e. if you are using Rythmbox or VLC (or any music player) close it, just so the soundcard is free to be used by firefox. This is all basic fundamentals here. All Linux drivers are only available to one program at a time, unless some tweaking and destroying is done with the drivers and the kernel...:eek:

Anyways, you should also make sure to have the latest flash player installed. And be sure to let things install peacefully, try to avoid using multiple programs when installing things...:)

---

### Post by ghostwalk.with.me on 2008-06-04
> **no1cares said:**
> speakers work and here sound when i play music from computer.....
I went to youtube and it said mozilla needs new software to watch this video or whatever. (the bar at top that appears when u need something to view a webpage).. it messed up somehow, cant explain how, i was doing other things while it was going and it just messed up... the video works but no sound.... 

need to know how to re-install the new software to watch the video. i know that is the problem.....

Sometimes the audio drivers tend to act a wee bit snarky. Usually, it occurs when you finish one audio application and jump directly into another. I have a feeling it doesn't have to do with the flash plugin, but may have something to do with pulse audio. Have you tried going into Preferences -> Sound?

---

### Post by no1cares on 2008-06-05
not sure why but went into Prefrences --> switch the last one from alsa to sigmaltel, and youtube works.....

***[COLOR="Lime"]SOLVED[COLOR="Black"][/COLOR][/COLOR]***

---

### Post by Toshibawarrior on 2008-06-05
Good to know it worked for you! :)

---

