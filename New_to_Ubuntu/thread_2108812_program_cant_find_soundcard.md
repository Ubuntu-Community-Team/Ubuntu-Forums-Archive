---
title: "program cant find soundcard"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by nycap on 2013-01-25
i am trying to run a program in ubuntu 12.10 (on dell inspiron 1525) that was written/released i believe for version 10.04.  

the error i get is:
```
Error, couldn't open /dev/audio
ioctl reset error 
ioctl speed error 
ioctl stereo error 
ioctl setfmt error 
Audio In/Out Device: /dev/audio
```

so is there anything i can do?  is there anyway to get legacy support for /dev/audio? anything short of trying to modify the program but i will try to change the code if i have too.

Thanks a bunch.

---

### Post by TheFu on 2013-01-25
The libraries have changed a bunch since then.  To see which devices are available, I use [B]
$ aplay -l[/B]

This is based on ALSA sound system.  I think /dev/audio might be pulse audio, so you'll need to get that loaded if there is any hope (which there may not be anyway).  There is an **ubuntu sound troubleshooter** - google will find it.

---

### Post by nycap on 2013-01-25
this is what is available:

```
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

how do we use this info?  thanks

---

### Post by nycap on 2013-01-25
went to the trouble shooter page; added the libraries just in case one was missing.  restarted, ran program, same error.   I am sure the sound card is recognized and working properly.  

Like I said before.  The problem is the the program was written for ubuntu 10.04 and as was said, /dev/audio was for a previous sound controlling software (if thats what you call it).   I think OSS was used then? I am not sure, please correct me if I am wrong.  

Is there anyway to put OSS on 12.10?   Or if its Pulse, then can we put that on 12.10.    Thanks a bunch.

---

### Post by TheFu on 2013-01-25
> **TheFu said:**
> The libraries have changed a bunch since then.

That means libc, other system libraries, sound libraries and probably most of the libraries used by whatever program you are trying to use again.

Is there **any** way, perhaps, but it depends on your skill.  Can you get the source code for the program and port it forward to 12.10?

Some quick googling on my part didn't provide much hope.  What is the name of the specific program? If you put that into the title, perhaps someone else has solved this exact issue?

Sorry, I don't know the answers.

---

### Post by nycap on 2013-01-25
The name of the program is DSD (digital speech decoder).   i have found posts about this same program but i have not found a fix.  

I would think that changing the code to run on 12.10 would be the best option; especially if /dev/audio is the only problem shouldnt be that bad to fix.  i cant get a hold of the author who could probably fix this easily.  Should we get this thread moved to a more appropriate forum if this is what i have to do?

---

### Post by TheFu on 2013-01-26
> **nycap said:**
> The name of the program is DSD (digital speech decoder).   i have found posts about this same program but i have not found a fix.  

I would think that changing the code to run on 12.10 would be the best option; especially if /dev/audio is the only problem shouldnt be that bad to fix.  i cant get a hold of the author who could probably fix this easily.  Should we get this thread moved to a more appropriate forum if this is what i have to do?

I looked up that program. Seems to be something related to HAM radio.
At some point it seems to have violated patents where I live, so I will not help in creating that tool, but I can advise.  

No, I don't like software patents, but that isn't a law that I will cross.

The source code seems to be available on sourceforge [http://sourceforge.net/projects/dsdmbelib/](http://sourceforge.net/projects/dsdmbelib/) according to google. Comments say that it uses only POSIX, so that means it should compile on almost any UNIX-like platform and even MS-Windows.  Other comments say that it uses ALSA, but I can't tell if those are true or not.

You will need to recompile everything for all the new libraries on 12.xx systems. Much has changed since 10.xx Ubuntu. Someone with C programming experience will probably be needed unless the README files are exceptional.  On some ham radio forums, I saw lots of people say that recompiling was easy ... in 2010. That is a good sign, but they may have been C-wizards at their day jobs too.

This might help too
[http://stackoverflow.com/questions/11347346/alsa-equivalent-to-dev-audio-dump](http://stackoverflow.com/questions/11347346/alsa-equivalent-to-dev-audio-dump)

At least the source code is available.

Good luck.

---

### Post by nycap on 2013-01-26
thanks for everything.  i was able to apply a patch and the program runs now.  again thanks for everything.

---

