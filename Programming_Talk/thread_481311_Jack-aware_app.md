---
title: "Jack-aware app"
date: 2007-06-22
forum: Programming Talk
---

### Post by tenzindorje on 2007-06-22
I would like to write a JACK-aware app that takes a MIDI stream as input and outputs the same
MIDI stream with MIDI key numbers altered, for microtonal retuning. This will be a simple app that
simply looks up the old value in an array, e.g.
    int lookupTable[128] = {...};
    int oldKey = 60;
    int newKey = lookupTable[oldKey];

The app can be written in any language (C, C++, Java, Ruby, etc.), but needs to be viewable
in the QJackCtrl patch window.

---

### Post by FuturePast on 2007-06-22
Hmm. Is this a question?

---

### Post by christhemonkey on 2007-06-22
Your app does not need to be at all JACK aware if you are doing midi.
(At present) MIDI I/O is actually done by ALSA.
The Midi tab on Qjackctl is actually the ALSA midi connections.


For information on using ALSAs midi API see this tutorial:
[http://www.alsa-project.org/~frank/alsa-sequencer/](http://www.alsa-project.org/~frank/alsa-sequencer/)



However in the coming months/weeks/years the JACK Midi API should stabilise so applications can use it instea of ALSA midi.
Some already do (dino is th only one that comes to mind!)

I suggest you subscribe to LAD and LAU and post there.
[http://lad.linuxaudio.org/subscribe/lau.html](http://lad.linuxaudio.org/subscribe/lau.html)
[http://lad.linuxaudio.org/subscribe/lad.html](http://lad.linuxaudio.org/subscribe/lad.html)

You will be probably be writting in C or C++ for an audio application.

Specifically the library for jackmidi is jack/types.h included in versions of jack >= 102.something (you have to specify  jack midi when compiling so the .deb packages for ubuntu (and debian!) do not include support for it atm)

The jack midi api is documented here:
[http://jackaudio.org/files/docs/html/midiport_8h.html](http://jackaudio.org/files/docs/html/midiport_8h.html)

And the general JACK api docs are here:
[http://jackaudio.org/files/docs/html/index.html](http://jackaudio.org/files/docs/html/index.html)



I also suggest if this is your first venture into programming that you start with something simple as audio applications are *very* complex (generally).

---

