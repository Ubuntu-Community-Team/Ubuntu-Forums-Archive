---
title: "Requesting advice on creating a program for discerning between various audio streams"
date: 2008-10-05
forum: Programming Talk
---

### Post by runesvend on 2008-10-05
Hello all!

I'm interested in creating a program for Linux that can be used to test if one is able to discern between two or more audio streams of varying qualities. I basically want to design a program that can play back and instantly shift between different audio files.

Let's say I for example have three files of the same song, one in 44.1kHz 16 bit PCM, another in 96kHz 24 bit PCM and a third in 192kHz 24 bit PCM. I wish to create a program that can be given the paths of these three files, play them back, and be able to switch between these audio streams instantly (or almost instantly).

I'm curious if one is able to discern between 44kHz audio and 96kHz audio and perhaps 192kHz audio, and the only good way to do this, as I see it, is to have a program that can instantly switch between the different audio streams between which one wishes to determine if a difference is audible.

I would really appreciate if someone could point me in the direction of how to accomplish this. I don't have any Linux programming experience though. I've written some programs for Windows; a program to send files from one computer to another using Winsock, a program for cutting MP3 files without re-encoding, and a program for setting the ID3 tags of multiple MP3 files, to mention my past main projects. All created using MS Visual Studio. But I migrated to Ubuntu about two and half years ago and now I don't have much interest in programming for Windows.

I imagine programming for Linux isn't too different from Windows-programming, but I have no idea if there are some available libraries to use that can accomplish the above, so I would appreciate some input on this. :)

Thanks in advance!

Rune Svendsen

---

### Post by gnusci on 2008-10-06
I just can point you to some pages:


[http://www.linuxjournal.com/article/6735](http://www.linuxjournal.com/article/6735)
[http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture](http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture)
[http://www.alsa-project.org](http://www.alsa-project.org)

[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)
[http://www.opensound.com](http://www.opensound.com)

Give them a look first... good luck!

---

