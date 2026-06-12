---
title: "Audacity/lame library puzzle"
date: 2006-09-29
forum: Programming Talk
---

### Post by brn on 2006-09-29
This question was discussed here a month or so ago...

> reyw05
January 24th, 2006, 02:21 PM
I'm trying to export a sound clip as mp3 so I can use it as a ringtone on my phone, but I can't locate the "libmp3lame.so" to do this. I've compiled and installed the lame-3.97 package, and I was just wondering where I could find the file. Thanks!
gord

...however I'm still confused.  Like reyw05, I compiled lame 3.97 and it works.  But *libmp3lame.so* required by Audacity is nowhere to be found nor is any library file remotely resembling it.  I can get by using Audacity to capture and store raw or wav data and then using lame for the conversion but now I'm curious about this very elusive library routine.  All net searches so far show lots of people looking for it but no one saying "here it is".

---

### Post by doobit on 2006-09-29
> **brn said:**
> This question was discussed here a month or so ago...



...however I'm still confused.  Like reyw05, I compiled lame 3.97 and it works.  But *libmp3lame.so* required by Audacity is nowhere to be found nor is any library file remotely resembling it.  I can get by using Audacity to capture and store raw or wav data and then using lame for the conversion but now I'm curious about this very elusive library routine.  All net searches so far show lots of people looking for it but no one saying "here it is".

The library you can use has a slightly different name extention. I'm not at my Ubuntu machine at the moment, but I remember that in Audacity you had two choices under the menu to select the Lame library and you need to pick the second choice. I think it's called extended library or something like that, and pick libmp3lame.so.o.

---

### Post by Zimmer on 2006-10-06
> **doobit said:**
> The library you can use has a slightly different name extention. I'm not at my Ubuntu machine at the moment, but I remember that in Audacity you had two choices under the menu to select the Lame library and you need to pick the second choice. I think it's called extended library or something like that, and pick libmp3lame.so.o.

Install liblame0 from multiverse via Synaptic, then in Audacity preferences find File formats> MP3 export and you should find the LAme codec in /usr/lib

---

### Post by gintan on 2007-06-17
As doobit says, the lib name is libmp3lame.so.0

To locate it in Audacity, 
1. go to Edit > Preferences > File Formats
2. click on Find Library then 'Yes'
3.  click on 'Only libmpslame.so' and change to 'Extended Libraries'
4. Scroll waaaay along and select the libmp3lame.so.0 file

Worked for me.

---

### Post by davosba on 2008-04-11
use synaptic to install liblame0

---

