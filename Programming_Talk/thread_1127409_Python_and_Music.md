---
title: "Python and Music"
date: 2009-04-16
forum: Programming Talk
---

### Post by Swenghk on 2009-04-16
I wanted to know if there was a way to play music in python...

And if so, where would I have to put the .wav files (or whatever python prefers) in order for python to play them

---

### Post by OutOfReach on 2009-04-16
Well Python itself can't play audio files, you need to utilize an external library such as pygame (pygame has an audio module) to play the audio

---

### Post by s.fox on 2009-04-16
Hi,


You can find information about Python audio here: [http://wiki.python.org/moin/Audio/](http://wiki.python.org/moin/Audio/)

-Ash R

---

### Post by stevescripts on 2009-04-16
Snack is a nice sound library, although I use it with tcl/tk - it should be pretty much to same to use Python....

Snack: [http://www.speech.kth.se/snack/](http://www.speech.kth.se/snack/)

If you want something small and already done, d/load:
[http://www.stevescripts.com/software/tsp](http://www.stevescripts.com/software/tsp)

A single file linux executable sound player.

Steve

---

### Post by Swenghk on 2009-04-16
How do I load up the tsp into my program? Is that even possible?

---

### Post by Swenghk on 2009-04-16
And How do I install Snack? I have never installed a module before (if thats even what snack is)

---

### Post by stevescripts on 2009-04-16
tsp is a single file linux executable - it has everything you need (including the Snack library)  should be a simple matter of chmod +x and run - Please let me know if it does *not* work for you.

If I can make some time - I may go ahead and do a python program using Snack ...

Hope this helps a bit.

Steve

---

### Post by stevescripts on 2009-04-16
Swenghk - ahh... so what you really want (it appears after reading your other thread),
is a way to play a sound file from a terminal based Python program...

My initial replay was to point out Snack, and a ready made small solution for playing sound files.

So, you should seriously look into the response from Ash R.

Steve

---

### Post by Swenghk on 2009-04-16
Alright, thanks for your help!

---

