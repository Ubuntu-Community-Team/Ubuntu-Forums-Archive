---
title: "Audio problems"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by MickW on 2013-10-05
Hi  
 

 I wasn't sure where to post this as it is about audio recording, but as I am a virtual Linux noob, I thought maybe it would be best to post it in the beginners section – chances are I am making some fairly basic mistakes!
 

 So I am trying to use an old PC to do some recording and I am using Hydrogen, Ardour and VMPK to lay down a rhythm track and am going to record guitars onto the track after that using a USB mic.  The problem is I have no clue how to configure the various software packages so that they will talk to each other. I have installed some other software as well (PulseAudio/Lmms/Qsynth/Audacity) and I have a feeling through reading a few other posts on the subject, that this can cause conflicts and problems with sound.  Are there any of these that I can/should uninstall?  I know Audacity and Ardour more or less do the same job so maybe one of them can go.
 

 As far as I can tell VMPK is using Timidity to connect to the sound library and I was trying to use Jack to do all of the connnections but this I cannot seem to do.
 

 One thing I have noticed is that I can use Hydrogen on its own with no issues but it seems to kill the audio for all other applications and I have to reboot if I want to listen to something with VLC or on youtube etc.  Also I can't replay any audio in Audacity once I have run Hydrogen as it freezes almost instantly that I start to play the track.  Once I reboot all these other applications run fine.  Not sure if this is related to the other problems but thought it worthy of a mention.
 

 By the way, the only reason I need VMPK is to lay down a bass line, as I don't have a bass guitar.  Is there some way I can record a bass line on a six string electric and then drop it down an octave?  I know that is a bit of a flaf but as these are just rough demos I am quite happy to get the tracks down in as simple a way as possible
 

 Thanks in advance for any assistance
 

 All the best
 

 MickW

---

### Post by philinux on 2013-10-05
I'm a noob too at audio recording using ubuntu. But if I were to start I reckon I would install ubuntu studio version.

[http://ubuntustudio.org/tour/audio/](http://ubuntustudio.org/tour/audio/)

There's also plenty of support [http://ubuntustudio.org/support/](http://ubuntustudio.org/support/)

---

### Post by Rob Sayer on 2013-10-05
Rather than installing ubuntu studio I'd probably just find out what it came with and install that.

You may have a problem with unmet dependencies in your codec libraries.  Have you installed ubuntu-restricted-extras (or maybe, like me, kubuntu-restricted-extras because I like the kde desktop)?  It will install a decent set of codec libraries and is one of the first things you should install in ubuntu.

---

### Post by MickW on 2013-10-07
Hi 

Thanks for the replies.  Can I just clarify - if I install Ubuntu Studio (which comes with everything I have already installed plus a little more) will that automatically be configured so that all the separate component packages will work together without any issues?

Also, Rob, if I do download all the packages separately could you tell me why that would be preferable to installing Ubuntu Studio?  

I do have ubuntu-restricted-extras installed.

I have looked at the download page and it looks like this is actually a version of Ubuntu which is effectively a standalone operating system - have I got that right?

---

