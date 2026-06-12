---
title: "Webcam doesn't work with skype"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by Simpleasy on 2012-07-04
Hi everyone,

I just installed skype, and I seem to have a problem with my webcam. At first it didn't seem to work at all, so after a bit of research I downloaded Cheese, and there it works perfectly. 
However, when I opened skype and tested it there, I got nothing. It was all black.
I did some more research, and as someone suggested, I opened skype with this code:

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```(I have no idea what it does exactly, since I am quite new to linux.)
When testing it again, it gave me better results than before, but the webcam is still nowhere from being useable. The image that I got was all noise, except for all the way on the top. About 10% of the whole screen (the top, as said before), gave me the image I was looking for.

As everyone probably understands, I want to use the entire image captured by my webcam, not just the top 10%, so any help is welcome.

Here is some extra information in case anyone wants to know:
webcam: trust WB5400
linux distro: Ubuntu 12.04
Skype version: the latest (since I downloaded it today)

EDIT:
When I doubleclick the testing screen, I still get the same noise and all that (in fullscreen) but in the terminal, this line shows up:

libv4l2: error allocating conversion buffer

I don't know if that's relevant, but I thought I'd mention it just to be sure

---

### Post by daslinkard on 2012-07-27
What kind of web cam are you using?  Is it built in or external?

---

