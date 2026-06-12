---
title: "wav loader c++"
date: 2007-08-07
forum: Programming Talk
---

### Post by richardhp on 2007-08-07
im trying to make a simple command line program that will play wav files. i've written some code that successfully reads in the file header data and the first chunk of sound data. how do i then use the sound data and play it out of the speakers? is there some way of accessing the sound buffer or are there some specific drivers/libraries i have to use?

---

### Post by rbprogrammer on 2007-08-07
i cant help you in figuring it out, but i think i might be able to help you with were to find out what you need..  hopefully

i read somewhere that if you wanted to work with sound you had to write data to the sound device. for instance:
```
echo data >> /dev/snd
```
or something like that.

hope that leads you to the right place, or *sorry if it doesnt*..

---

### Post by Lster on 2007-08-07
You could also consider SDL_Mixer; I found that very easy to play .Wavs with.

---

### Post by joe_bruin on 2007-08-07
The simplest way to output sound is to write it to /dev/dsp.  This is a simple wav device that usually accepts 44.1khz 16-bit stereo sound.  You can just open(2) it and write(2) the wav data out to it if it's in the correct format.  Make sure you write an even number of samples at a time.

This is the old and easy way to do things.  However, it does not play nice with the rest of the system since only one process can open /dev/dsp at a time.  At this point it becomes a lot more complicated.  There is the new Linux sound system, ALSA.  You can link libalsa into your application and use it.  Above ALSA, Ubuntu 7.04 uses ESD, the Enlightenment Sound Daemon (a sound mixer daemon).  You can interface with libesd.  Finally, there is the Gnome (or KDE) sound system, although if you're not writing a Gnome or KDE program, you probably don't want to use these.  If you are writing a GUI program, you should consider using your chosen toolkit's standard sound interface.

Linux audio continues to be a total mess, so good luck.

---

### Post by richardhp on 2007-08-11
ok thanks. i know this is an ubuntu forum but i want it to be cross platform so what would i do in windows??

---

### Post by n.aggel on 2007-08-11
basically i don't think it is that easy to be crossplatform, unless you use an appropriate framework{like QT-but i am not sure if it has classes for playing sounds}.

If on the other hand you use {directly} the underline infrastructure of the OS...you will write platform specific software.....

---

### Post by richardhp on 2007-08-11
thanks

---

### Post by the_unforgiven on 2007-08-11
You can use [SDL]("http://www.libsdl.org") if you want it to be cross-platform.
Here is a simple example of how to use audio API of SDL:
[http://www.libsdl.org/intro.en/usingsound.html](http://www.libsdl.org/intro.en/usingsound.html)

---

