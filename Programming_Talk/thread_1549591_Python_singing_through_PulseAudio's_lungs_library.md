---
title: "Python singing through PulseAudio's lungs library?"
date: 2010-08-10
forum: Programming Talk
---

### Post by teryret on 2010-08-10
Hello all, I'm preparing to start a new hobby project in Python. It will be a music player that doesn't suck (Winamp being the only music player I've ever given the "doesn't suck" title to, and I'm sick of having to use wine just to play music).

Disclaimer:  I'll be the first to say I don't yet have a clear idea of how audio works in Linux, so please be gentle.  I'm by no stretch new to programming, but this is my first time targeting Linux.

One of my main concerns is this vague sense of doom associated with the name PulseAudio and the fact that there is no python-pulseaudio bindings package in the repositories as there is for alsa.  Is that a problem?  The wikipedia article (that I'll admit to only partially understanding) suggests that the alsa interface will work because pulseaudio exposes a shim interface that looks like alsa, but that talking directly to pulseaudio is also possible.  The latter seems like the much cleaner and more featureful solution (since pulseaudio probably isn't going anywhere in the forseeable future), but in my googling I've not seen any real information on how that direct interface works... which leads me to believe either I'm asking the wrong question or nobody has done this in python yet (which seems unlikely).

Does anyone have any good resources that I could go read?  Or perhaps a high level description of how this whole sound thing works and what parts of it I will need to familiarize myself with?

Thanks in advance for whatever help I can get!

---

### Post by teryret on 2010-08-12
Bump!  Doesn't anyone know how audio programming works in ubuntu?

---

### Post by smartbei on 2010-08-13
I guess I would go for creating your own python interface to pulseaudio through a simple wrapping of the pulseaudio APIs.

See [http://0pointer.de/lennart/projects/pulseaudio/doxygen/](http://0pointer.de/lennart/projects/pulseaudio/doxygen/) for the pulseaudio side of the API, and something like [http://www.swig.org/](http://www.swig.org/) for wrapping to python.

Alternatively, you could use the ctypes module from python to wrap the pulseaudio shared libs:
```

# plays a pcm file using the pulseaudio simple interface. Works for me (that is, generates noise for me - I 
# This is a simple translation of example code that exists in the above pulseaudio link from C to python.
did not have a pcm file to test it on).
import ctypes
import struct
import sys

pa = ctypes.cdll.LoadLibrary("libpulse-simple.so.0")

PA_STREAM_PLAYBACK = 1
PA_SAMPLE_S16LE = 3
BUFFSIZE = 1024

def main(filename):

    fd = open(filename, 'rb')
    
    pat_sample_spec = ctypes.c_buffer(struct.pack("LLB", PA_SAMPLE_S16LE, 44100, 2))
    error = ctypes.c_int(0)
    s = pa.pa_simple_new(0, filename, PA_STREAM_PLAYBACK, 0, "playback", ctypes.byref(pat_sample_spec), 0, 0, ctypes.byref(error))
    if s == 0:
        raise Exception("Could not create pulse auio stream!")
    
    while True:
        latency = pa.pa_simple_get_latency(s, ctypes.byref(error))
        if latency == -1:
            raise Exception("Get Latency failed!")

        #print("%0.0f usec" % (latency))

        buf = ctypes.c_buffer(fd.read(BUFFSIZE))
        if len(buf) == 0:
            break

        if pa.pa_simple_write(s, buf, len(buf), ctypes.byref(error)):
            raise Exception("Could not play file...")

    if pa.pa_simple_drain(s, ctypes.byref(error)):
        raise Exception("Could not simple drain! ...")
    
    pa.pa_simple_free(s)    

if __name__ == "__main__":
    if len(sys.argv) != 2:
        print("Usage: ./%s <filename to play>" % (sys.argv[0],))
    else:
        main(sys.arg[1])

```
It runs on my computer, but I did not have a pcm file lying around to test it on. (On anything else it generates noise).

I strongly suggest you look into the Exaile project - they have a working music player written in Python that works quite well with PA.

---

### Post by teryret on 2010-08-13
Awesome, that link to the PA API is exactly what I needed, thank you so much!  Apparently ubuntuforum no longer has the thank you button, otherwise I'd click it.

Per your suggestion I've got Exaile downloaded, it's got some major room for improvement, but I suspect looking at the code will make my life a thousand times easier.  Thanks again!

---

