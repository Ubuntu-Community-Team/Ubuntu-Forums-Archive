---
title: "Testers needed for a small PyQt thingie"
date: 2008-08-12
forum: Programming Talk
---

### Post by Bachstelze on 2008-08-12
Hi everyone ;)

So as the title says, I'd like a few people to test a PyQt thing I've been coding for the last few days. It was mostly a learning experience but I thought I'd better code something that could be useful, so it's a GUI for the Nero Digital AAC encoder for Linux, and because I suck at finding names, it's called NALG (which stands for Nero AAC for Linux GUI).

You can get it [here](ftp://itsuki.fkraiem.org/pub/NALG/).

There is a README but here's in short what you need in order to use it:

* PyQt 4, which you can install in Ubuntu by installing the package [font="Courier New"]python-qt4[/font].

* The encoder itself, you can get it from [here](http://www.nero.com/eng/down-ndaudio.php).

Then extract the archive, browse to the dir and run it with

```
python NALG.py
```

The rest should be pretty straightforward. Thanks to anyone that will spend a bit of his time testing it ;)

*EDIT: oh, and there's a small cookie in the code, for those of you who like searching for them ;)*

---

### Post by eldeingles on 2008-08-29
hi there,
everything followed and double-checked...not workin
i'm on mint elyssa

i'd like it to be truly working

PS: i'm so stupid! didn't give it permissions! NOW it really WORKS!!!
A progress bar would be most welcome!
Thnx

---

### Post by Bushi on 2009-05-31
Hello HymnToLife,the following download link is broken [ftp://itsuki.fkraiem.org/pub/NALG/](ftp://itsuki.fkraiem.org/pub/NALG/)
I couldn't find anywhere on the web the file "NALG-0.1rc2.tar.gz" (is it the latest version?)..please can you share it once again? thanks :)

---

### Post by Bachstelze on 2009-05-31
Link fixed.

As you can see, development has been pretty much stalled for a long time, but I plan to start working on it again soon. ;)

---

### Post by Bushi on 2009-06-02
> **HymnToLife said:**
> Link fixed.

As you can see, development has been pretty much stalled for a long time, but I plan to start working on it again soon. ;)
Thank you.
I think that the most interesting features that you could add are the following ones,quoting from the readme:

* Encoding from other source formats. The Nero AAC encoder only supports
WAV as input, so this is the only input format supported so far. Both
ffmpeg and mplayer will be supported for decoding of the input file.

 * Queued encodings. So far, only one encoding can be run at a time. The
queued encoding feature will allow the user to schedule several encoding
jobs, and run them all in one step later.

  * Encoding in other formats like Vorbis to make this a more universal audio encoding GUI? 
(look at Be Light,Be Happy,megui etc..you can add something like lame mp3,vorbis,wav,ac3,speex etc)
Bye :)

---

