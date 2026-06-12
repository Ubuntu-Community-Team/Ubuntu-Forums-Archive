---
title: "Converting Midi files to mp3 using ubuntu/Linux"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by The Voice on 2012-01-28
I have over 10.000 midi files on a CD which I wish to:
 sort, edit and save in MP3 format for burning to CD.
I have tried LMMS,Audacity, Timidity and followed all the advice from google searches, but to no avail.
My Timidity version is 2.13.2, which when open, is very basic.
I have tried to install LAME and have found the recommended versions are already installed on my computer.
My Audacity version is 1.37.
I gave up with this as I could'nt tell if anything was happening in Audacity or what I was doing!
I f there is a way to convert midi files to MP3 that actually does'nt involve me taking a bachelors in Network architect design or something similar, I would appreciate knowing about it as I am at the end of my patience with this.

Cheers!
James M :rolleyes:

---

### Post by kc1di on 2012-01-28
Hi,

the link below gives one way to do it. I've tried it and it works well.

[http://www.ehow.com/how_5114457_convert-midi-mp-ubuntu.html]("http://www.ehow.com/how_5114457_convert-midi-mp-ubuntu.html")

---

### Post by mcduck on 2012-01-28
> **ron999 said:**
> Hi
This is the type of command for converting mid to mp3:-
```
timidity -Or -o - filename.mid | lame -r - filename.mp3
```

For more options look at:-
```
timidity -h
```
and
```
lame --longhelp
```

Test it with one or two midi files, then script it for the whole 10,000.

---and in addition to this, make sure you've got a decent sound font installed for Timdity to use, at least if your purpose is to get a decent audio file instead of being just able to hear the MIDI songs...

---

### Post by andrew.46 on 2012-02-11
If your copy of vlc supports midi playback you will be able to convert to mp3 using its gui:

```

andrew@skamandros~$ **[COLOR="Red"]cvlc -l | grep fluidsynth[/COLOR]**
VLC media player 2.0.0-rc1 Twoflower (revision 1.2.0-pre4-238-g9cc771b)
  fluidsynth             FluidSynth MIDI synthesizer

```

---

### Post by sadaruwan12 on 2012-02-11
You can use the Sound Converter to convert your files it has GUI and very easy to use a well.

---

