---
title: "dependencies"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by h_howee on 2008-04-22
Im sry if this has already been posted before, I've spent the last hour and a half installing dependencies for [http://home.gna.org/subtitleeditor/](http://home.gna.org/subtitleeditor/) and I'm nowhere near having them all installed. I urgently need to get this working for an assignment that's due this thursday and I need to get some sleep as well so I don't have much time for searching.
Each dependency keeps leading on to more dependencies. My question is, how am I supposed to get them all installed?
I'm also getting
> 
checking for GSTREAMER... no
***
*** Error! you need to have : 
*** gstreamer-0.10
*** gstreamer-base-0.10
*** gstreamer-plugins-base-0.10
***

and I already have gstreamer installed

---

### Post by dynamethod on 2008-04-22
you may need the gstreamer-dev packages

---

### Post by sdennie on 2008-04-22
Actually, subtitleeditor is included in the universe repository on at least Ubuntu 7.10 and above.  You should be able to install it using:

```

sudo apt-get install subtitleeditor

```

If you are building it manually because you need a more up to date version, should be able to install all the things you need to build it with:

```

sudo apt-get build-dep subtitleeditor

```

---

### Post by h_howee on 2008-04-22
The above worked. It installed without any errors but it won't open and I just lost my sound.

[geocities.com/file_storage00/Screenshot.png](geocities.com/file_storage00/Screenshot.png)

When I try to run it, it shows up for a second on the bottom panel but then just disappears without any error messages.

edit:
nvm, the sound works, it's just the volume control
I still can't get the subtitleeditor to run though

edit 2:
If i want to run it through the termin, do I type in "subtitleeditor"?
> 

howard@howard-desktop:~$ subtitleeditor
subtitleeditor: /home/howard/mono-1.9/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
subtitleeditor: symbol lookup error: subtitleeditor: undefined symbol: _ZN7pcrecpp6no_argE


---

### Post by sdennie on 2008-04-22
In the end did you install it by building your own version or installing via "apt-get install"?  Either way, if you could open a terminal and run "subtitleeditor" and post the output, that would be useful in figuring out why it isn't starting.

---

### Post by h_howee on 2008-04-22
I did it with sudo apt-get install

I just tried running through the terminal a minute ago, I edited my last post and put the error message there, but either way, here it is again...

> 
subtitleeditor: /home/howard/mono-1.9/lib/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
subtitleeditor: symbol lookup error: subtitleeditor: undefined symbol: _ZN7pcrecpp6no_argE


---

### Post by sdennie on 2008-04-22
Did you custom compile and locally install a version of mono?  You could try doing this in a terminal and then try to start subtitleeditor again:

```

mv ~/mono-1.9 ~/mono-1.9.bak

```

---

### Post by stchman on 2008-04-22
> **h_howee said:**
> Im sry if this has already been posted before, I've spent the last hour and a half installing dependencies for [http://home.gna.org/subtitleeditor/](http://home.gna.org/subtitleeditor/) and I'm nowhere near having them all installed. I urgently need to get this working for an assignment that's due this thursday and I need to get some sleep as well so I don't have much time for searching.
Each dependency keeps leading on to more dependencies. My question is, how am I supposed to get them all installed?
I'm also getting

and I already have gstreamer installed

Yes that program is included in the repositories.

```
sudo apt-get install subtitleeditor
```

---

### Post by h_howee on 2008-04-22
That fixed the first error

> 
subtitleeditor: symbol lookup error: subtitleeditor: undefined symbol: _ZN7pcrecpp6no_argE

I fixed the second error by downgrading to pcre 7.5

I can open subtitleeditor but I can't load a video from it...

> 
Failed to create a GStreamer 'decodebin'

Please check your GStreamer installation



edit:
Fixed by installing gst-plugins-base-0.10.19 from source...

now I'm getting 
> 
A AVI demuxer plugin is required to play this stream, but not installed.


---

### Post by h_howee on 2008-04-22
I'm just trying random things now...

When installing gst-plugins-0.8.12 from source, I get "error: no GStreamer found"


edit:
ME == MAD
it took less than an hour to set up a subtitle editor on windows xp and that would have been about 2 minutes if I had known from the start that the file I was trying to open was corrupt.

---

