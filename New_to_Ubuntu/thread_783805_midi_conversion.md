---
title: "midi conversion"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Periswell on 2008-05-06
hi

i was wondering, as audacity will not let me do it, if there is a program to change the midi files (from rosegarden) to other types of music formats eg .ogg .wav or .mp3. help will be most appreciated.

-josh

---

### Post by warbread on 2008-05-06
A midi file is just a set of events, not music.  You can play that file through an instrument, record it in something like Ardour and then export that as an .mp3 or whatever you want.

---

### Post by Periswell on 2008-05-06
thanks lots.

---

### Post by 3rdalbum on 2008-05-06
Timidity is a software MIDI renderer, and it can play its output directly into an AIFF, FLAC or Ogg Vorbis file.

Should be something like this:

```
timidity -Ow -o destination.wav source.mid
```

I don't have any MIDI files at hand at the moment so I can't try this out for you. If you get stuck, Timidity has a man page.

---

### Post by Periswell on 2008-05-06
im afraid it does not work, oh well, thanks for trying. or if you want to have a go at my problem i have attached a .zip file with the midi inside that i want to convert.

---

