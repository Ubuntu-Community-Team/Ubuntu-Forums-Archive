---
title: "Text to speech?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Xm3buX on 2008-09-15
Are there any text to speech programs, kind of like Microsoft sam for windows?

Thanks.

---

### Post by Dr Small on 2008-09-15
Try espeak. It's in the repositories.

---

### Post by -Zeus- on 2008-09-15
orca is installed by default.

---

### Post by humhum on 2008-09-15
> **Xm3buX said:**
> Are there any text to speech programs, kind of like Microsoft sam for windows?

Thanks.

xxxxx@xxxxx:~$ apt-cache search text speech
**espeak - A multi-lingual software speech synthesizer**
**ksayit - a frontend for the KDE Text-to-Speech system**
**kttsd - a Text-to-Speech system for KDE**
libgnome-speech-dev - GNOME text-to-speech library (development headers)
libgnome-speech7 - GNOME text-to-speech library
brltty-flite - Access software for a blind person using a braille display
cowsay - A configurable talking cow
eflite - Festival-Lite based emacspeak speech server
**epos - Text-to-speech system**
**festival - General multi-lingual speech synthesis system**
festival-freebsoft-utils - Festival extensions and utilities
festival-hi - Festival text to speech synthesizer for Hindi
festival-mr - Festival text to speech synthesizer for Marathi
festival-te - Festival text to speech synthesizer for Telugu (te) language
festlex-ifd - Italian support for Festival
festvox-kallpc16k - American English male speaker for festival, 16khz sample rate
festvox-kallpc8k - American English male speaker for festival, 8khz sample rate
festvox-kdlpc16k - American English male speaker for festival, 16khz sample rate
festvox-kdlpc8k - American English male speaker for festival, 8khz sample rate
ihu - Qt VoIP softphone with an own, encrypted protocol
jbofihe - A parser for the lojban language
kttsd-contrib-plugins - the KDE Text-to-Speech system
libtime-human-perl - convert localtime() format to "speaking clock" time
lsr - The Linux Screen Reader for GNOME
recite - English text speech synthesizer
screader - Screen reader using software or hardware speech synthesizer
festvox-rablpc16k - British English male speaker for festival, 16khz sample rate
festvox-rablpc8k - British English male speaker for festival, 8khz sample rate
gnome-speech-dectalk - GNOME text-to-speech library (Fonix DECtalk engine support)
gnome-speech-swift - GNOME text-to-speech library (Cepstral swift engine support)
w3-recs - Recommendations of the World Wide Web Consortium (W3C)
libmythes-dev - simple thesaurus library (development files)

I have used some, but I don't remember wich... :P

---

### Post by cariboo on 2008-09-15
If I run a search for text to speech in synaptic, I find:

epos
espeak
fesatival
kttsd

Plus another three screen readers. Take your pick.

Jim

---

### Post by Xm3buX on 2008-09-15
Right, it seems espeak is already installed. How do I access it?

Thanks.

---

### Post by Flare183 on 2008-09-15
Open a termnial and type in espeak.

---

### Post by t0p on 2008-09-15
> **Xm3buX said:**
> Right, it seems espeak is already installed. How do I access it?


espeak is a command line utility, very easy to use. Just open a terminal and type **espeak** followed by required options...

**From the man page:**
>  -f <text file>
              Text file to speak

       --stdin
              Read text input from stdin instead of a file


So, the command

```
espeak -f words.txt
```

would cause espeak to "read" the textfile words.txt.

---

