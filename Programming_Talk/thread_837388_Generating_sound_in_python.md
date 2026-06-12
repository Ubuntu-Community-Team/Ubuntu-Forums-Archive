---
title: "Generating sound in python"
date: 2008-06-22
forum: Programming Talk
---

### Post by thepopasmurf on 2008-06-22
Using python, how can you generate tones or sounds in ubuntu?

---

### Post by LaRoza on 2008-06-22
What library are you using?

For a simple beep, you just print "\a".

---

### Post by thepopasmurf on 2008-06-22
Well, that's what I'm trying to find out, which libraries should I use

---

### Post by WW on 2008-06-22
To play existing sounds (e.g. .wav or .ogg), pygame has a convenient interface.  For more advanced audio manipulation, take a look at [pyaudio](http://people.csail.mit.edu/hubert/pyaudio/).  A list of more possibilities is available in the [audio section of the python wiki](http://wiki.python.org/moin/Audio/).

---

### Post by rlameiro on 2008-06-22
Hi, well I had the same problem that you had, I found a library that does what you want, the problem is that the generator sound class is recent and there is to little documentation about it, but it works!
the library name is tksnack and you can find it here.

[http://www.speech.kth.se/snack/](http://www.speech.kth.se/snack/)

there is a code snippet that shows how to use it, at daniweb's page. it is here
[http://www.daniweb.com/code/snippet414.html](http://www.daniweb.com/code/snippet414.html)

should you have any question shout, I am in any means an expert, but will try to help, with my minimal knowledge.

---

