---
title: "Working with MIDI data"
date: 2010-02-12
forum: Programming Talk
---

### Post by DSan4444 on 2010-02-12
Hello everyone,

So I have a typical MIDI controller/keyboard hooked up via USB to my linux box and I'm trying to figure out the best way to capture incoming MIDI data from it.  I know data is being read in correctly as I used the program Pure Data ([http://puredata.info/](http://puredata.info/)) to test it, so now I just want to be able to write a program (in c++, c, or Python) to capture it and display it to the terminal in realtime as I press keys and turn knobs...etc.

At the moment I have been messing around with the alsa/asoundlib.h header and I understand that the ALSA api has a interface for MIDI devices?  

Any help on the matter would be greatly appreciated.  Eventually I want to be able to integrate this program with other applications so I can have MIDI data controlling other events.

---

### Post by gordintoronto on 2010-02-12
If you run Synaptic and search for MIDI, you will get dozens of programs, most of which are not relevant.  The first one which might be useful to you is Fluidsynth.  Midish is another.  Have a look for yourself.

---

### Post by DSan4444 on 2010-02-13
ah ok thanks.  If anyone has personal experience programming with MIDI in real time that I would love to hear about it as well.

---

### Post by DSan4444 on 2010-02-18
Actually I found exactly what I was looking for in an ALSA program called aseqdump.

aseqdump -l shows me what ports my MIDI device is on and then aseqdump -p outputs the data coming from that port in real time in nicely formatted text so I get note, velocity, cc information easily.

---

### Post by sharpdust on 2010-02-18
Just as a side note, I've used KMidimon in the past to do what you're doing. It was very straightforward.

Furthermore, I've done some midi programming in Java which provide a nice API to work with.

---

