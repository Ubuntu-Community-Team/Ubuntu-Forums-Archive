---
title: "In Need Of Knowledge"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Trzone on 2008-07-02
I have a friend who would love to use ubuntu, he has no need to use windows.  However, he requires a program that would rip audio cd files into the .m4a or apple lossless audio format.  If anyone would know how to do this, it would be greatly appreciated!

---

### Post by pytheas22 on 2008-07-02
I'm not positive, but I think you could do it with Audacity, or possibly avidemux.  Maybe some one else knows a program that will do it for sure though.  I don't have time to research now but if no one else responds, I will try to get back with a definite answer for you (if I don't respond within a couple of days, please remind me!); I'm sure there's a way to do it.

Also, the people in the Multimedia and Video subforum would know better than those in this one.

---

### Post by wolfen69 on 2008-07-02
as per [Here]("http://soundconverter.berlios.de/") you can convert to m4a with soundconverter. available in the ubuntu repos. make sure to get the proper codecs first though.

---

### Post by bab1 on 2008-07-02
I don't think Audicity will rip CD's.  I belive iTunes will do what you need.

---

### Post by Rhubarb on 2008-07-02
Sound Juicer (that comes with Ubuntu by default) has support for ripping into this format.
You may have to install the correct mpeg4 codecs to do this (I'm not exactly sure which package you need).
In Sound Juicer, go to the preferences, then in output format choose "CD Quality (MPEG-4 audio)".

> **bab1 said:**
> I don't think Audicity will rip CD's.  I belive iTunes will do what you need.
There is no way you need to use iTunes to rip audio CDs into this format.

---

### Post by bluepowder7 on 2008-07-02
i think you can also do it using plain ol' VLC.  open the cd, and stream the output to a set of files using the mp4a transcode option.  might have to do each audio track separately, though - i haven't tried it yet for audio CDs, but i've used it for DVDs.

---

### Post by Trzone on 2008-07-03
It's the format .m4a, it's the lossless one, not the lossy one (.aac)  Any idesa?  Or am i confused about the whole AAC thing?

---

### Post by snick525 on 2008-07-03
I know someone already said this, so it might not be helpful.  But you really can just use iTunes.

I promise it will do what you need.

---

### Post by zalberico on 2008-07-03
I'm assuming you need these formats so that your friend can use his/her ipod with ubuntu right?

How new is the ipod?  If its one of the very new ones I think they have a hash that makes them only work with itunes, so I don't know if they'll work with gnulinux.

I don't know any programs that rip apple lossless besides itunes, however itunes will not natively run in linux. (Apple lossless is a proprietary format).

If you don't need those formats for an ipod I would suggest the formats .ogg(ogg vorbis - lossy) and FLAC (lossless).  They're both open source compression formats and have superior sound quality.

If you're in the market for a new portable media device I'd recommend Cowon they have fantastic support for gnulinux and work like a flash drive for importing and extracting music.

[http://www.jetaudio.com/](http://www.jetaudio.com/)  I have the Cowon D2

There are many programs in gnulinux that can rip cds to mp4 but again if its a new ipod you may not be able to get them on it.

Oh and aac is just the itunes store bought format that has drm on it, to get rid of it burn it to a disk and reimport.

Good Luck!

---

### Post by snick525 on 2008-07-03
If you install Wine, or have it already installed, you can install iTunes.

[http://www.winehq.org/site/howto]("http://www.winehq.org/site/howto")

Installing iTunes after that is fairly straightforward (from [http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/]("http://www.linuxscrew.com/2007/09/19/install-itunes-72-in-ubuntu-and-other-linux-distros/")):

 1. Run in terminal:
      ```
wine iTunesSetup.exe
```
   2. Install iTunes as you do it in Windows or Mac OS X
   3. Run it with command:
     ```
 wine ~/.wine/drive_c/Program\ Files/iTunes/iTunes.exe
```

---

### Post by Trzone on 2008-07-03
I've been able to successfully set up itunes and import cds using wine.  Problem solved? But if we can PLAY apple lossless codecs and since copyright law is not a global law, can't someone develop an encoder that can be encorporated into sound converter or sound juicer?  Just a thought...

---

