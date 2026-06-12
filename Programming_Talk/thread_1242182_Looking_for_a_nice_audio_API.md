---
title: "Looking for a nice audio API"
date: 2009-08-16
forum: Programming Talk
---

### Post by J05HYYY on 2009-08-16
Hello all,

I want to find a portable audio api with full-duplex capabilities. So far I have looked at the following (and their apparent problems):

[COLOR="Navy"]**Csound(s) API** - In my opinion, the best to use.[/COLOR]
[B]
OpenAL[/B] - Has many implementations, some are more maintained than others. Code has to be re-written for each separate platform. Some implementations do not provide support for other platforms. [(See here: I added to their wish list)]("http://connect.creativelabs.com/openal/Lists/Wishlist/DispForm.aspx?ID=40&Source=http%3A%2F%2Fconnect.creativelabs.com%2Fopenal%2FLists%2FWishlist%2FAllItems.aspx")

**PortAudio** - Hardly any documentation, fairly low level, I have a problem in full duplex mode regarding the number of channels ( error -9998 ) whilst running the test program patest_wire. (mailing list has been informed)

**FMOD** - Has a nasty license.

**SDL_Mixer** - No audio capture.

**OpenSL ES** - Used for Embedded Systems

**Audiere & Java Sound API** - "real men program in C" :P

Any more I should consider using? Gimme your opinions on these.

---

### Post by JordyD on 2009-08-16
> **J05HYYY said:**
> [B]
OpenAL[/B] - Has many implementations, some are more maintained than others. Code has to be re-written for each separate platform. Some implementations do not provide support for other platforms.

No. OpenAL is [cross-platform]("http://connect.creativelabs.com/openal/OpenAL%20Wiki/Platforms.aspx"). The only OpenAL implementation (that I know of) is called [OpenAL]("http://connect.creativelabs.com/openal/default.aspx").

On ubuntu:
```
sudo apt-get install libopenal-dev
```
will install everything you need for OpenAL development with C or C++.

And OpenSL|ES is for *E*mbedded *S*ystems.

**EDIT:** Sorry, by implementation, you mean from platform to platform, don't you? In that case, yes, there are many implementations.

---

### Post by J05HYYY on 2009-08-16
yeah, as in OpenGL Soft ... which can't be run on OS X

what about having to change code to reflect the platform?

see here:
```
"Refer to the table below to view how the alutLoadWAVFile call differs between platforms." [OpenAL Tutorial]("http://www.edenwaith.com/products/pige/tutorials/openal.php")
```

I thought the whole point in portability was the fact I didn't have to re-write code in order to re-compile on a different platform?

---

### Post by soltanis on 2009-08-16
Unfortunately audio across platforms is one hell of a headache. Linux alone has a billion different implementations, and it kind of goes downhill if you want to take your code elsewhere. I would suggest using OpenAL, which, though as you pointed out barely qualifies the word "portable" is probably going to be the most portable solution you find.

---

### Post by J05HYYY on 2009-08-16
I joined the mailing list for portaudio and sent a question regarding the error. Just gotta hope they get back to me. To be fair, I am reluctant to start coding using OpenAL for the reasons stated before.

What about JACK applications? Does it need a server present at run-time?

**EDIT:**

I got an e-mail back from Ross Bencina saying that the "patest_wire" palaver could be due to the device not supporting stereo output.

I tested "patest_leftright" which correctly played two different tone sine waves alternating between the left and right channel.

I sent another e-mail regarding my findings based on the fact I got stereo output through "patest_leftright" but not "patest_wire".

**EDIT 2:**

Still nothing back from the portaudio developers. I have managed to get full-duplex using the csound programming language - It apparently has an audio API for C (and it is completely written in C).

I will continue to keep looking into this, so far, it looks promising :)

**EDIT 3:**

The csound program works fine ... Whilst using the csound API[ I hit a problem]("http://www.csounds.com/node/482")

I also found a post from someone who used csound and got the [dreaded -9998 error message with portaudio.]("http://www.csounds.com/node/353")

**EDIT 4:**

I'm a little confused as to how to install the csound library. I think there is a [debian package for the development files]("http://packages.debian.org/search?keywords=csound") but I think they might be installed automatically [when it is built from source]("http://www.csounds.com/manual/html/BuildingCsound.html"). I'm not sure; so I'll try making some kind of installer with wget and see what happens.

**EDIT 5:**

I realized today that I was making a silly (and rather annoying) mistake. Basically I wasn't linking to libcsound properly and gcc wasn't very good at using the "-l" prefix. All in all csound is literally awesome. In my opinion it is the best cross platform audio library and it is also bleedin' good program. I can't wait to start some real coding now ... coz I got there in the end (if this is the end) :P

---

### Post by jacky.alcine on 2011-02-06
Could you demonstrate how one would go about playing and recording audio?
:popcorn:

---

### Post by worksofcraft on 2011-02-06
I have used [gstreamer]("http://gstreamer.freedesktop.org/") and there was a really good [gstreamer tutorial for python]("http://pygstdocs.berlios.de/pygst-tutorial/index.html") I think they have them for other languages too.

---

