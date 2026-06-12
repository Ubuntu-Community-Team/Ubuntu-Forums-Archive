---
title: "[C]: Mix 2 wav files into one file"
date: 2008-04-13
forum: Programming Talk
---

### Post by MblKiTA on 2008-04-13
I need to write a program which takes 2 input wav files, mixes them into one stream and writes down the result to the output file. The question is - where to start? ;) May be there is a library which can do this easily? Thanks in advance :)

---

### Post by LaRoza on 2008-04-13
What do you mean "mix"?

You can easily create one file from them (just append both to the same file), and it is likely easy to "mix" them alternative writing segments of the files.

I don't know what that would do to them, as I don't know the insides of the format.

Either of those options can be used with the standard library (specifically, the functions declared in stdio.h)

---

### Post by WW on 2008-04-13
I don't know if this is the easiest way, but the command-line program [sox](http://sox.sourceforge.net/) can do this.  The ubuntu package is also called [sox](http://packages.ubuntu.com/gutsy/sox).

EDIT: If you really want to write your own program, the library [libsndfile](http://www.mega-nerd.com/libsndfile/) is a good place to start.  The relevant Ubuntu packages are libsndfile1 and libsndfile1-dev.

---

### Post by MblKiTA on 2008-04-13
> **LaRoza said:**
> What do you mean "mix"?

Mix - I mean to combine them.. not the one after another, but "mix" them together :guitar:

> **WW said:**
> I don't know if this is the easiest way, but the command-line program [sox](http://sox.sourceforge.net/) can do this.  The ubuntu package is also called [sox](http://packages.ubuntu.com/gutsy/sox).

EDIT: If you really want to write your own program, the library [libsndfile](http://www.mega-nerd.com/libsndfile/) is a good place to start.  The relevant Ubuntu packages are libsndfile1 and libsndfile1-dev.
thanx a lot, i'll take a look :)

---

### Post by LaRoza on 2008-04-13
> **MblKiTA said:**
> Mix - I mean to combine them.. not the one after another, but "mix" them together :guitar:

Does it have to play afterwords?

---

### Post by MblKiTA on 2008-04-14
> **LaRoza said:**
> Does it have to play afterwords?

Yes.. 2 wav files should be mixed to the output wav file, which is ready to be played

---

### Post by POW R TOC H on 2008-04-14
[http://www.borg.com/~jglatt/tech/wave.htm](http://www.borg.com/~jglatt/tech/wave.htm)
Read this. Then try to write your own library for reading & writing wav files... That would be a good start :D
In fact, now you got me interested, and I'm gonna try this myself :) If I do it before you, I will post the code...

---

### Post by Zugzwang on 2008-04-14
@OP: WW's tip is the best. Here's an excerpt from the man page of sox:

```

sox -m music.mp3 voice.wav mixed.flac

    mixes together two audio files.

```

There's also a list of audio formats supported and it's quite impressive.

@Laroza: Mixing means that you hear both sounds at the same time. This is for example needed for studio recording: Before the song gets burned on CD, all the individual tracks (drums, bass, vocals, guitars, etc.) are mixed together to a stereo track.

@POW R TOC H: This seems to be overkill. There's already a library called libsnd. So if that's well documented enough, no need to re-invent the wheel.

---

### Post by MblKiTA on 2008-04-29
yeah, sox is very nice command-tool :) :guitar:
```

sox -m -v 0.9 01_l.wav -v 0.1 01_r.wav out.wav

```
This code does what I wanted.
Thanks a lot guys :)

---

