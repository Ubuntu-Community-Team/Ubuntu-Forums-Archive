---
title: "Python sound"
date: 2010-08-17
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-17
I read that Python programmers have a winsound package when running on Windows, but I can't find one for Linux.

Can anyone recommended a good way to include simple sounds in a Python application?

---

### Post by StephenF on 2010-08-17
A casual Google search reveals an ossaudiodev module.

[http://docs.python.org/library/ossaudiodev.html](http://docs.python.org/library/ossaudiodev.html)

---

### Post by worksofcraft on 2010-08-17
Thanks :)
I'm still struggling to get a single squeak out of that one :(

Meanwhile I was kind of hoping someone knows of something more platform independent and portable.

---

### Post by worksofcraft on 2010-08-17
So like, I copied this bit someone else posted out there on the www
```

file='ding.wav'
from wave import open as waveOpen
from ossaudiodev import open as ossOpen
s = waveOpen(file,'rb')
(nc,sw,fr,nf,comptype, compname) = s.getparams( )
dsp = ossOpen('/dev/dsp','w')
try:
	from ossaudiodev import AFMT_S16_NE
except ImportError:
	if byteorder == "little":
		AFMT_S16_NE = ossaudiodev.AFMT_S16_LE
	else:
		AFMT_S16_NE = ossaudiodev.AFMT_S16_BE

dsp.setparameters(AFMT_S16_NE, nc, fr)
data = s.readframes(nf)
s.close()
dsp.write(data)
dsp.close()

```

but when I run it all I get is:
```

from: can't read /var/mail/wave
from: can't read /var/mail/ossaudiodev
./sound.py: line 4: syntax error near unexpected
./sound.py: line 4: `s = waveOpen(file,'rb')'

```

and well... quite frankly I have no idea what it is doing in /var/mail and I can't say much else makes sense to me either :(

---

### Post by StephenF on 2010-08-17
Looks like you had a little problem with copy and paste picking up some invisible character. I copied and pasted from the forum and using a 16 bit little endian wav file for ding.wav I'm getting audio playback.

Also /var/mail? What are you talking about?

---

### Post by worksofcraft on 2010-08-17
> **StephenF said:**
> Looks like you had a little problem with copy and paste picking up some invisible character. I copied and pasted from the forum and using a 16 bit little endian wav file for ding.wav I'm getting audio playback.

Also /var/mail? What are you talking about?

Hum IDK, those were the error messages I got when I tried to run it. Didn't make any sense to me what-s-ever  :( However I'll try copy/pasting again ;)

Meanwhile I found this really good article about using gstreamer: 
[http://www.jonobacon.org/2006/08/28/getting-started-with-gstreamer-with-python/](http://www.jonobacon.org/2006/08/28/getting-started-with-gstreamer-with-python/) and that seems to be working a treat if anyone else is having problems with making sounds from Python programs :)

---

### Post by km0r3 on 2010-08-18
> **worksofcraft said:**
> 
```

from: can't read /var/mail/wave
from: can't read /var/mail/ossaudiodev
./sound.py: line 4: syntax error near unexpected
./sound.py: line 4: `s = waveOpen(file,'rb')'

```and well... quite frankly I have no idea what it is doing in /var/mail and I can't say much else makes sense to me either :(

As far as I can see you inserted a `'` at the end of the line, which is why you get a syntax error.

Here is some code I have found for reproducing sound with the (great) gstreamer library.


```
# [SNIPPET_NAME: Playing a Pipeline]
# [SNIPPET_CATEGORIES: GStreamer]
# [SNIPPET_DESCRIPTION: Construct and play a pipeline]
# [SNIPPET_AUTHOR: Tiago Boldt Sousa <tiagoboldt@gmail.com>]
# [SNIPPET_LICENSE: GPL]


#!/usr/bin/python

import pygst
pygst.require("0.10")
import gst
import sys
import gobject

#Create a player

class Player:
    def __init__(self, file):
        #Element playbin automatic plays any file
        self.player = gst.element_factory_make("playbin", "player")
        #Set the uri to the file
        self.player.set_property("uri", "file://" + file)

        #Enable message bus to check for errors in the pipeline
        bus = self.player.get_bus()
        bus.add_signal_watch()
        bus.connect("message", self.on_message)

    
    def run(self):
        self.player.set_state(gst.STATE_PLAYING)

    def on_message(self, bus, message):
        t = message.type
        if t == gst.MESSAGE_EOS:
            #file ended, stop
            self.player.set_state(gst.STATE_NULL)
            loop.quit()
        elif t == gst.MESSAGE_ERROR:
            #Error ocurred, print and stop
            self.player.set_state(gst.STATE_NULL)
            err, debug = message.parse_error()
            print "Error: %s" % err, debug
            loop.quit()

#Execution starts here

#Specify your file bellow 
#It can be any video/audio supported by gstreamer
file = "/usr/share/sounds/gnome/default/alerts/bark.ogg"

player = Player(file)
player.run()
loop = gobject.MainLoop()
loop.run()
```

---

### Post by worksofcraft on 2010-08-18
Thanks Km0r3 :)

gstreamer definitely seems to be the way to go. I was coincidentally just trying to fathom a few details, like detecting when a file has finished playin. Your code provides a number of insights which is great because details of using gstreamer seem still a bit hazy to me :oops:

However strangely, when I ran this, it created an image of the next window I clicked in  :confused:

Then I moved #!/usr/bin/python to the first line and got an error message:
```

./pipe.py: line 11: syntax error near unexpected token `"0.10"'
./pipe.py: line 11: `pygst.require("0.10")'
cjs@cjs-ubuntu:~/Desktop/gstreamer$ ./pipe.py
Error: Could not open resource for reading. gstgiosrc.c(324): gst_gio_src_get_stream (): /GstPlayBin:player/GstGioSrc:source:
Could not open location file://ding.wav for reading: Operation not supported

```

So I'll be experimenting a bit more immanently!

---

### Post by km0r3 on 2010-08-18
You're welcome, mate. :)

> **worksofcraft said:**
> 
```

Error: Could not open resource for reading. gstgiosrc.c(324): gst_gio_src_get_stream (): /GstPlayBin:player/GstGioSrc:source:
Could not open location file://ding.wav for reading: Operation not supported

```

Smells like you set the value for `file` to an invalid path. Try setting it to something like /home/<your_username>/valid_sound_file.ogg .

Also be sure to read this great [Python GStreamer Tutorial]("http://pygstdocs.berlios.de/pygst-tutorial/index.html").

---

### Post by worksofcraft on 2010-08-18
Thanks for that link.

What I discovered is that gstreamer "playbin" works great with .ogg files but can't play .wav files, while "filesrc" seems to work for them both.

---

