---
title: "[SOLVED] sound effects/change theme music"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-02
is it possible to change the theme music both the drums and the following jingle to these mp3 clips I have of space ship tracking beam generators and plasma stream cannon shots?  I might  like to add some other sound effects too elsewhere though i haven't given it much thought.  Is this possible?

---

### Post by tjwoosta on 2008-07-02
system-preferences-sound

then click the sounds tab


Edit: i think the files have to be .wav

you should be able to convert .mp3 to .wav with audacity (applications-add/remove then click show all available applications then search audacity)

---

### Post by wolfen69 on 2008-07-02
or use Soundconverter. but you must have the required codecs first.

---

### Post by bhadotia on 2008-07-02
The codecs are ffmpeg, faad, flaac, lame etc. if you do not know.

---

### Post by tjwoosta on 2008-07-02
> The codecs are ffmpeg, faad, flaac, lame etc. if you do not know.

arent theese codecs part of the w32codecs?

if so you can add the medibuntu repository 
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

then do 
```
sudo apt-get install w32codecs
``` (or w64codecs for 64bit ubuntu)

---

### Post by bhadotia on 2008-07-02
> **tjwoosta said:**
> arent theese codecs part of the w32codecs?

if so you can add the medibuntu repository 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then do 
```
sudo apt-get install w32codecs
``` (or w64codecs for 64bit ubuntu)

Oh .. , I don't know whenever I do a fresh install of ubuntu just open up this link and pcopy and paste all the commands there in without even reading a word:) and that makes my ubuntu ready to face the world:
[http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia](http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia)

---

### Post by bhadotia on 2008-07-02
Or you can also do :
```
sudo apt-get install non-free-codecs
```
That will take care of the 32/64 bit issue.

---

### Post by adamogardner on 2008-07-02
ok  sorry, then , I found the files in .wav too so I'll just use those.  specifically now I'm going to download this robot girl who says shields activated and shields deactivated when I lock and unlock my screen respectively.  at least this is the beginning of my fantasy.  is it doable? how?

---

### Post by tjwoosta on 2008-07-02
hmm.. well just taking a quick look i dont see any way to play a sound when the screen is locked and unlocked

you can change the startup and shutdown sounds pretty easily though


(mine has a voice that says startup protocal activated and shudown sequence engaged)

here is an link to an awesome voice generator[http://www.research.att.com/~ttsweb/tts/demo.php]("http://www.research.att.com/~ttsweb/tts/demo.php")

---

### Post by bhadotia on 2008-07-02
Thanks for the link.

---

### Post by adamogardner on 2008-07-02
I thought this was "A do anything you can think of" operating system.  There must be a way from the terminal isn't there?  I want to give this machine life.  ok  marking as solved because A want to start a fresh title  incidently my location for sound effects is soundsnaps.com.  they have lots to choose from.  thanks everyone.  I got the "connection initiated" for start up, and "connection disengaged" for shutdown in a girl robot voice. I seem to have misfortune with things that I erase from my desktop (i like it clean) but then when I restart the application or picture is completely missing from my system.  If you know what I"m doing wrong I would love to know.

---

### Post by AlexanderDGreat on 2012-12-05
It's been 2012 - and the ONLY DECENT Google search for Ubuntu's Sound Effects Documentation is a 2008 thread.

Wow ubuntu!

---

### Post by overdrank on 2012-12-06
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

