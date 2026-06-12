---
title: "Does anybody want to write me a small program (serial port control)?"
date: 2007-05-04
forum: Programming Talk
---

### Post by musther on 2007-05-04
Let me get straight to the point:

I'm visually impaired, and I listen to books using a speech synth, I do this in a portable way with my bookcourier ([www.bookcourier.com](www.bookcourier.com) - for which somebody wrote a Linux transfer tool, thank god).  I would like to be able to use my old serial port synth to listen to books in Ubuntu.  

So, what I need is a simple program (can be command line or...  ...anything really) which will take in a large text file, parse it into sentences (or some smallish chunks) and then send them to the serial port one at a time, checking for a specific output command (which says that the synth has finished speaking) before sending the next.  

Additional required features are being able to stop, and resume from the same position, skip forward and back one sentence at a time (and maybe larger chunks), and close the program but have it remember the position in the text for next time.

I think the best thing to do would be for the system to take a copy of the required file, that can be modified to store current position etc.

It would be good if I could open several text files (not at the same time), and have different reading positions in each.  So I can open A, read about half, close, open B, read a bit, close, reopen A and have a saved reading position.

I don't really care how it's implemented, could be command line using bash and a text editor, a plugin for gedit (actually that would be a really great way), whatever, so long as it works.

So, if anybody would like to help, please let me know and I can give you more info.

Thanks for taking the time to consider helping me.

You can email me at [email]jmusther@gmail.com[/email]

-----EDIT----
I've just been looking at Gedit Plugins, I think a python plugin for gedit would be the best way to go - I think this will be required:
[http://sourceforge.net/projects/pyserial/](http://sourceforge.net/projects/pyserial/)

---

### Post by jmc1024 on 2007-05-04
I might be able to write what you need, but I'm really busy this time of year.  As a
temporary solution have you looked into festival?  It does a lot, but a couple of
things you may find useful: text file to synthetic speech and text file to audio file.
HTH,
Mark

---

### Post by musther on 2007-05-04
Yes I've looked at festival, and indeed that's what I use for small amounts of speech.  But the speech is diphone based, so it's quite good at slow speeds, and sounds quite human, but for extended listening it's not really any good (anyone who uses speech for computer access or reading extended text will know what I mean).  That's what lead me to digging out my old hardware synths, they're rule based and much more comfortable for long listening.

I appreciate that you can't help me now, but if you can at some point in the future I would really appreciate it.  Over to you.

---

