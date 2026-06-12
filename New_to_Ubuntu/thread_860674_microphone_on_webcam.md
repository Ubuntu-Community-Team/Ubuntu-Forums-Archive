---
title: "microphone on webcam"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by aestrivex on 2008-07-15
i recently got a Creative Live! Cam Video IM Pro VF0410 (USB device 041e:4063).

finally managed to get the video portion working with the uvcvideo driver and flashcam.


however, the audio device built into this webcam is not detected by any program (i figure its probably called USB audio device, but google searches have revealed that USB audio device seems to typically refer to an external sound card).


and i'm pretty sure i'm just missing something here.  what do i need to do to configure this microphone to function correctly?



a couple of questions i have about how it may function:

does the uvc driver include support for the microphone as well as the video?  if not, what other driver do i need to get?

is the problem outlined [here](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC) (pasted below) the problem?

> Starting at version 2.6.22, the Linux kernel includes a USB audio bug fix which triggers a (possibly identical to the above) bug in first and second generation Logitech webcams. Fortunately this one seems to have a workaround, although not a pretty one.

The webcam audio interface must be initialised before the video interface. Linux will by default initialise the video interface first, so you need to remove the uvcvideo.ko module from the /lib/modules subdirectory where it gets loaded automatically, and load it manually after plugging the webcam. 

it seemed to me on reading this that the problem above only refers to Logitech webcams.  if this is the issue, how do i fix it?

i have already configured my volume control to accept capture feeds.  the only device microphone that is detected, however, is "linux microphone," which i assume is the default ALSA system which doesn't actually exist because i don't have any hardware for it.


running hardy on x86_64 AMD.  i would love to get this working in order to interface with flash applications like stickam.

---

### Post by aestrivex on 2008-07-16
i'm bumping this once, and exactly once.

---

