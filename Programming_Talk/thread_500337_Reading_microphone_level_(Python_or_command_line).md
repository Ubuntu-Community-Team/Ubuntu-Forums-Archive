---
title: "Reading microphone level (Python or command line)"
date: 2007-07-13
forum: Programming Talk
---

### Post by cpcgm on 2007-07-13
To use my microphone as a sensor for the Player Robotics Device I need to get the value of the current volume, frequency or whatever as float but can't find a way to do that. Does anyone know either a python module or a command line program a similar output? Has anyone worked with sndpeek ([http://www.cs.princeton.edu/sound/software/sndpeek/](http://www.cs.princeton.edu/sound/software/sndpeek/)) and could that help?

---

### Post by dwblas on 2007-07-13
volume.py, an adesklet, imports ossaudiodev to do that.  The program is fairly straight forward.
[http://adesklets.sourceforge.net/desklets.html](http://adesklets.sourceforge.net/desklets.html)

---

### Post by cpcgm on 2007-07-13
Thanks for the answer. I looked into it but as far as I understand it it just displays the current setting of the system volume. I'm looking for a way to get the current volume in the room.

---

### Post by dwblas on 2007-07-13
Mine is several year old, but line 213 in mine starts with
# Get the current system volume
def get_volume(self) :

---

### Post by cpcgm on 2007-07-13
Jep. But that just gives you, well, the current system volume which is (I tried it) the master volume set via the volume control on the gnome-panel or alsamixer.

---

### Post by CShadowRun on 2009-01-06
```

#!/usr/bin/python
## This is an example of a simple sound capture script.
##
## The script opens an ALSA pcm for sound capture. Set
## various attributes of the capture, and reads in a loop,
## Then prints the volume.
##
## To test it out, run it and shout at your microphone:

import alsaaudio, time, audioop

# Open the device in nonblocking capture mode. The last argument could
# just as well have been zero for blocking mode. Then we could have
# left out the sleep call in the bottom of the loop
inp = alsaaudio.PCM(alsaaudio.PCM_CAPTURE,alsaaudio.PCM_NONBLOCK)

# Set attributes: Mono, 8000 Hz, 16 bit little endian samples
inp.setchannels(1)
inp.setrate(8000)
inp.setformat(alsaaudio.PCM_FORMAT_S16_LE)

# The period size controls the internal number of frames per period.
# The significance of this parameter is documented in the ALSA api.
# For our purposes, it is suficcient to know that reads from the device
# will return this many frames. Each frame being 2 bytes long.
# This means that the reads below will return either 320 bytes of data
# or 0 bytes of data. The latter is possible because we are in nonblocking
# mode.
inp.setperiodsize(160)

while True:
	# Read data from device
	l,data = inp.read()
	if l:
		# Return the maximum of the absolute value of all samples in a fragment.
		print audioop.max(data, 2)
	time.sleep(.001)

```

Enjoy!

---

### Post by Zugzwang on 2009-01-07
Dear OP, for both of your data (frequency and volume) you will actually need to interpret concrete sample data you captured from your audio-in device. 

For getting the volume, the result heavily depends on your definition of "volume". The post above uses the most simple one, there are also others which measure the energy of the waveform, etc.

Getting the frequency is actually not simple at all. There might be libraries who attempt to do this, but don't expect too much!

---

### Post by cmonkey on 2009-01-08
> **CShadowRun said:**
> ```

#!/usr/bin/python
## This is an example of a simple sound capture script.
##
## The script opens an ALSA pcm for sound capture. Set
## various attributes of the capture, and reads in a loop,
## Then prints the volume.
##
## To test it out, run it and shout at your microphone:

import alsaaudio, time, audioop

# Open the device in nonblocking capture mode. The last argument could
# just as well have been zero for blocking mode. Then we could have
# left out the sleep call in the bottom of the loop
inp = alsaaudio.PCM(alsaaudio.PCM_CAPTURE,alsaaudio.PCM_NONBLOCK)

# Set attributes: Mono, 8000 Hz, 16 bit little endian samples
inp.setchannels(1)
inp.setrate(8000)
inp.setformat(alsaaudio.PCM_FORMAT_S16_LE)

# The period size controls the internal number of frames per period.
# The significance of this parameter is documented in the ALSA api.
# For our purposes, it is suficcient to know that reads from the device
# will return this many frames. Each frame being 2 bytes long.
# This means that the reads below will return either 320 bytes of data
# or 0 bytes of data. The latter is possible because we are in nonblocking
# mode.
inp.setperiodsize(160)

while True:
	# Read data from device
	l,data = inp.read()
	if l:
		# Return the maximum of the absolute value of all samples in a fragment.
		print audioop.max(data, 2)
	time.sleep(.001)

```

Enjoy!
Great!  This is exactly what I've been looking for too.  I was about to hack apart sndpeek and use SWIG to pythonize it, but this is far better.

---

### Post by short_cake on 2009-05-11
very thanks
but there is a problem i really faced
:confused::confused: 

Traceback (most recent call last):
  File "C:\Users\TOSHIBA\Desktop\voice.py", line 10, in <module>
    import alsaaudio, time, audioop
ImportError: No module named alsaaudio

how can i solve this:confused:
would somebody help me
thanks any way.

---

### Post by CShadowRun on 2009-05-11
> **short_cake said:**
> very thanks
but there is a problem i really faced
:confused::confused: 

Traceback (most recent call last):
  File "C:\Users\TOSHIBA\Desktop\voice.py", line 10, in <module>
    import alsaaudio, time, audioop
ImportError: No module named alsaaudio

how can i solve this:confused:
would somebody help me
thanks any way.

Your on windows, this is a ubuntu support forum! This code will not work on windows.

---

### Post by Zugzwang on 2009-05-12
> **CShadowRun said:**
> Your on windows, this is a ubuntu support forum! This code will not work on windows.

short_cake, you can however try to reimplement the functionality using some portable library, like [pySDL]("http://pysdl.sourceforge.net/"), for example.

---

### Post by short_cake on 2009-05-12
is there any code like  this for windows,
and i really need like this in symbian mobiles like nokia.
:confused::confused:
thanks for replying.

---

### Post by Zugzwang on 2009-05-13
> **short_cake said:**
> is there any code like  this for windows,


It's everything but unlikely that there is. However, I'm afraid that this is certainly the wrong forum for you, so use google to find the answer (or a more suitable forum).

A short google search yielded that there are indeed platform-independent python modules for sound i/o. You can reprogram the algorithm presented above with them:

[http://wiki.python.org/moin/Audio/](http://wiki.python.org/moin/Audio/)

---

### Post by hackeron on 2009-05-17
Seems setperiodsize is ignored which is stopping me from using this suggestion :(

```

>>> import alsaaudio
>>> inp = alsaaudio.PCM(alsaaudio.PCM_CAPTURE,alsaaudio.PCM_NONBLOCK,'pcm.saa7134_0')
>>> inp.setchannels(2)
2
>>> inp.setrate(32000)
32000
>>> inp.setformat(alsaaudio.PCM_FORMAT_S16_LE)
2
>>> inp.setperiodsize(160)
4000
>>> while True:
...     l,data = inp.read()
...     if l:
...         break
... 
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
alsaaudio.ALSAAudioError: Capture data too large. Try decreasing period size
>>> 
>>> 
>>> inp.setperiodsize(40)
4000
>>> while True:
...     l,data = inp.read()
...     if l:
...         break
... 
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
alsaaudio.ALSAAudioError: Capture data too large. Try decreasing period size
>>> 

```

---

### Post by cpcgm on 2009-05-18
That's how I did it two years ago:

[http://www.dominikmayer.com/player](http://www.dominikmayer.com/player)

---

### Post by geek228 on 2010-12-15
user@user-pc:~/sndpeek-1.3/src/sndpeek$ make linux-alsa 
make -f makefile.alsa
make[1]: Entering directory `/home/user/sndpeek-1.3/src/sndpeek'
gcc -D__LINUX_ALSA__ -D__LITTLE_ENDIAN__ -I../marsyas/ -O3 -c RtAudio.cpp
RtAudio.cpp: In member function ‘virtual bool RtApiAlsa::probeDeviceOpen(int, RtApi::StreamMode, int, int, RtAudioFormat, int*, int)’:
RtAudio.cpp:4015: error: ‘INT_MAX’ was not declared in this scope
make[1]: *** [RtAudio.o] Error 1
make[1]: Leaving directory `/home/user/sndpeek-1.3/src/sndpeek'
make: [linux-alsa] Error 2 (ignored)


I am trying to compile the sndpeek 1.3 in ubuntu,but this error message keeps on coming each time the program is compiled.......can anyone pls help me solving this error....

---

### Post by Arndt on 2010-12-15
> **geek228 said:**
> user@user-pc:~/sndpeek-1.3/src/sndpeek$ make linux-alsa 
make -f makefile.alsa
make[1]: Entering directory `/home/user/sndpeek-1.3/src/sndpeek'
gcc -D__LINUX_ALSA__ -D__LITTLE_ENDIAN__ -I../marsyas/ -O3 -c RtAudio.cpp
RtAudio.cpp: In member function ‘virtual bool RtApiAlsa::probeDeviceOpen(int, RtApi::StreamMode, int, int, RtAudioFormat, int*, int)’:
RtAudio.cpp:4015: error: ‘INT_MAX’ was not declared in this scope
make[1]: *** [RtAudio.o] Error 1
make[1]: Leaving directory `/home/user/sndpeek-1.3/src/sndpeek'
make: [linux-alsa] Error 2 (ignored)


I am trying to compile the sndpeek 1.3 in ubuntu,but this error message keeps on coming each time the program is compiled.......can anyone pls help me solving this error....

```
$ grep INT_MAX /usr/include/*
/usr/include/limits.h:#  define INT_MAX	2147483647

```

Some file needs to include limits.h, it seems.

---

### Post by janpetel on 2012-11-24
This post is still of use; I might actually start to like Python ;-)

I was up to the point of trying to reuse Audacity's monitoring meter, but this is so much simpler...

tx

---

