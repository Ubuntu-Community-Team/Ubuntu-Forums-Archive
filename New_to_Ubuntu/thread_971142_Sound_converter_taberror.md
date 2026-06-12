---
title: "Sound converter: taberror"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Frenske on 2008-11-04
Hi I am using sound converter to change the music compression or extension. Now I have upgraded to 8.10, sound converter crashes every time with the following error:

```
francisco@ubu-desk:~$ soundconverter
SoundConverter 1.3.2
Traceback (most recent call last):
  File "/usr/bin/soundconverter", line 43, in <module>
    import pygtk
  File "/var/lib/python-support/python2.5/pygtk.py", line 41
    dir = os.getcwd()
                    ^
TabError: inconsistent use of tabs and spaces in indentation
francisco@ubu-desk:~$ 
```

Something to do with a function in python library. The command os.getcwd() seems to work in python. What could be wrong? If there any other good alternatives to sound converter I don't mind changing.

---

### Post by keplerspeed on 2008-11-04
Possibly reinstall soundconverter, I have upgraded to 8.10 and have had no trouble with soundconverter.

---

### Post by Frenske on 2008-11-05
Unfortunately that did not work and the error message suggests that the error is in the python library.

---

### Post by jcook793 on 2008-11-06
Yeah I'm getting the same error too...

---

### Post by drunkndog5 on 2008-11-12
I was getting this error and I did a complete removal, and then installed it again, and now it seems to be working OK.

---

### Post by Dr. Clock on 2008-11-16
I get the same error.
I tried completely removing sounconverter in the synaptic package manager
and installing soundconverter in the synaptic package manager,
but that didn't work.
Any other suggestions?

---

### Post by LoRaK on 2008-11-18
I tried purging soundconverter and reinstalling the python-gtk2 package, then reinstalling soundconverter. It worked.

I suppose reinstalling python-gtk2 was the crucial move here, as soundconverter did not work right after installing it for the first time ever, so it could not get corrupt or anything.

---

### Post by jpoRS on 2008-11-18
For those less experienced users, to use LoRak's method, open a terminal and enter
```

sudo apt-get remove soundconverter && sudo apt-get remove python-gtk2 && sudo apt-get autoremove && sudo apt-get install python-gtk2 && sudo apt-get install soundconverter
```

I haven't tried this personally, so use at your own discretion.

jim

---

### Post by Dr. Clock on 2008-11-20
Your ideas are note worthy(so I will save this web address into my
doc),
however I had already found and fixed the problem by the time
I saw your messages.
I didn't do what you guys did and suggested to do:
Here is basically what I did:
Some of this info I copy and paised here and added  what I did along side:
System -> Administration -> Software Sources
Click the tab that says "Third-Party Software".
Make sure those two boxes are checked,
however what worked for me was unchecking them.
Press close and agree to reload.

Open a terminal and run these codes, all though I am not sure which I used first,
so I would suggest using on then the other then the one you used first,
but I am still new to all of this.

sudo apt-get update

sudo apt-get upgrade


Below is where I got my info:
//////////////////////////
Here is where I got most of my info:
[http://ubuntuforums.org/showthread.php?t=755558&page=2](http://ubuntuforums.org/showthread.php?t=755558&page=2)

Here info on problems simular to the problems I was having on another hard
drive, in fact both hard drives with Ubuntu
(one with Ubuntu Hardy Heron upgraded to Intrepid)
and the other
(one upgraded from Hardy Heron to Intrepid to Ubuntu Studio Intrepid)
which all had to with the fact that I had
the Third-Party Software Tab checked during when I upgraded both Ubuntu Hardy Heron's:
[http://ubuntuforums.org/showthread.php?t=601300](http://ubuntuforums.org/showthread.php?t=601300)

and when I opened Soundconverter Soundconverter 
opened me to one of these webpages that lead me to the other webpage:
[http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/](http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/)

[http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)

Here is a note I made about visiting those pages
try installing:
GStreamer-lame
however I didn't end up installing GStreamer-lame through Synaptic Package Manager
instead I looked up GStreamer mp3 and installed:
Ubuntu Restricted Extras which made decoding mp3 files possible
and converting other audio formats into mp3.

Both hard drives with Ubuntu have soundconverter working
which both weren't working before.

---

