---
title: "C++ best high level sound library"
date: 2011-02-19
forum: Programming Talk
---

### Post by gufide on 2011-02-19
Hi, no one know what is the best high level 2d sound library in c++ to play ogg and midi? Thank

---

### Post by nickleboyblue on 2011-02-19
Look up sfml.  It's a full fledged media library, but it's easy to learn and it works really well.  In synaptic, it's called libsfml.  Download all the modules: audio, graphics, etc, and see what you think.

To compile a program that uses sfml, you must compile it with options to configure the specific modules your program uses.  See their website:

[http://www.sfml-dev.org/]("http://www.sfml-dev.org/")

---

### Post by hakermania on 2011-02-19
In your position I would use the pre-installed canberra-gtk-play (it's the one that plays the login sound)

You can call it through
```
#include <stdlib.h>
system("canberra-gtk-play -f /path/to/the/ogg/file&"); //the & is for just launching, otherwise the program will stack till the ogg file stops playing

```
I think this solution should be better if you don't want your program to be protable so as to run in other platforms... I wouldn't waste my time searching how to play ogg files through libraries while there is a pre-installed package playing them....

---

### Post by gufide on 2011-02-19
[QUOTE=SFML]
Can load and save standard sound formats : ogg, wav, flac, aiff, au, raw, paf, svx, nist, voc, ircam, w64, mat4, mat5         pvf, htk, sds, avr, sd2, caf, wve, mpc2k, rf64
[/QUOTE]
It didn't play midi :/


[QUOTE=hakermania]
I think this solution should be better if you don't want your  program to be protable so as to run in other platforms... I wouldn't  waste my time searching how to play ogg files through libraries while  there is a pre-installed package playing them....
[/QUOTE]
This will not allow multi-platform through windows and mac (doesn't matter if it don't allow multi-platform for windows  but I will prefer it)

---

### Post by nickleboyblue on 2011-02-19
If you want midi, you are going to have to find a library specifically dedicated to it, because midi is based on sequencer technologies that aren't even hinted at in traditional sound files.  If you want to process both midi and ogg in the same program, you will need two libraries.  If you're looking at cross-platform programming, you will most likely need at least three libraries (if you use sfml).  I do not know of any midi libraries for Linux that also work on windows or mac.

---

### Post by gufide on 2011-02-19
and witch library for linux you know for midi?

---

### Post by nickleboyblue on 2011-02-19
Alsa comes standard with several libraries (asoundlib, for one) that support midi.  See this link:

[http://tldp.org/HOWTO/MIDI-HOWTO-9.html]("http://tldp.org/HOWTO/MIDI-HOWTO-9.html")

I haven't found much documentation for the API, and I don't know if there is a viable c++ wrapper for it all yet.

---

### Post by worksofcraft on 2011-02-19
> **gufide said:**
> It didn't play midi :/


What you have to realize is that midi is not a sound format.
midi provides a stream of instructions that enable a music synthesizer to play the music... a bit like a musician reading the notes to play.

So midi files can't reproduce sounds like the human voice. To play a midi file you need an electronic synthesizer of some sort and of course some hardware has this capability built into the sound card and others struggle because they have to do it all in software.

So IMO you must decide if you want to make an application that plays generic sound files or one that synthesizes music :popcorn:

---

### Post by gufide on 2011-02-20
so... I'm better to translate my midi file to ogg?

---

### Post by KrishnaPG on 2011-03-17
For MIDI, there are few options: RtMidi, JDKMidi, PortMidi, TSE3 etc....
 
However, as indicated at [http://blogs.msdn.com/b/gpalem/archive/2011/03/17/alsa-driver-for-jdkmidi-with-rtmidi-on-linux-using-c-0x-futures.aspx](http://blogs.msdn.com/b/gpalem/archive/2011/03/17/alsa-driver-for-jdkmidi-with-rtmidi-on-linux-using-c-0x-futures.aspx) every one of them has few or other drawbacks.
 
If you are looking for pumping MIDI messages yourself with a sequencer consider the above. However, if you are looking for using Music Strings with MIDI notes (not MIDI bytes) then CFugue is your choice: [http://gpalem.web.officelive.com/CFugue.html](http://gpalem.web.officelive.com/CFugue.html)
 
CFugue lets you play MIDI with music notes such as A B C etc...
 
Its in active development and its source along with sample applications can be downloaded from: [http://sourceforge.net/projects/musicnote/files/](http://sourceforge.net/projects/musicnote/files/)
 
CFugue MIDI Music String Documentation can be found at: [http://musicnote.sourceforge.net/docs/html/pagemusicstring.html](http://musicnote.sourceforge.net/docs/html/pagemusicstring.html)

---

### Post by dodle on 2011-03-21
Please correct me if I am wrong, but I believe that [SDL_mixer](http://www.libsdl.org/projects/SDL_mixer/) can play both ogg and midi.

---

