---
title: "Burn subtitles into a video and edit subtitles."
date: 2008-08-15
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-08-15
I'm looking for software to burn my .srt subtitles into a video.

I'm also looking for software to edit subtitles.

I have no clue what to use.

What do you suggest?

[I]extra info:

I want to keep the file as an avi, I don't want to burn it to dvd. I know how to add subtitles using vlc, that's not what I'm looking for.[/I]

---

### Post by AllanPoe on 2008-08-15
[http://gnome-subtitles.sourceforge.net/](http://gnome-subtitles.sourceforge.net/)

[http://www.icewalkers.com/Linux/Software/528020/Subtitle-Editor.html](http://www.icewalkers.com/Linux/Software/528020/Subtitle-Editor.html)

---

### Post by billgoldberg on 2008-08-15
Thanks for pointing me to some editors.

Now Ijust need something to embed/burn them in the video.

---

### Post by SZ07 on 2008-08-16
With .avi files, you can only have hardsubs (i.e. the subtitles become a part of the actual video). If you make an .mkv file, you can have softsubs (the subtitles are included with the video, but are not a part of the video and so they can be turned off.

It looks like you are wanting to harcode subs in an .avi file. This process is relatively easy in windows, but in linux you are left with limited options.

You should be able to use programs like MEncoder or spumux (part of dvdauthor) to accomplish this but you will have to use command line (last time I checked there was still no GUI to accomplish such a task). Unfortunately, I have never encoded subs using these programs but this thread might help out:
[http://www.linuxquestions.org/questions/linux-software-2/command-line-video-text-overlay-650468/](http://www.linuxquestions.org/questions/linux-software-2/command-line-video-text-overlay-650468/)

---

### Post by nolan- on 2008-08-16
I just googled it after some commands in the above pages failed for me and I found one that worked on the Gentoo wiki.

[http://gentoo-wiki.com/TIP_MEncoder_Tips_and_Tricks](http://gentoo-wiki.com/TIP_MEncoder_Tips_and_Tricks)

It's about halfway down the page.

Good luck!

---

### Post by shirilover on 2008-08-16
Two more options here:

Editing subtitles: Aegisub -> [http://www.getdeb.net/category.php?id=12](http://www.getdeb.net/category.php?id=12)

Encoding subtitles onto video: Avidemux (in repo) or -> [http://www.getdeb.net/category.php?id=12](http://www.getdeb.net/category.php?id=12)

---

### Post by tubunu on 2009-02-07
> **SZ07 said:**
> With .avi files, you can only have hardsubs (i.e. the subtitles become a part of the actual video). 

Not true. If you use Devede, you can add subtitles to an avi file and turn them on/off as you wish.

---

### Post by RomanIvanov on 2009-02-07
Best application from my point of view - it helped me edit, change, split, .... with subtitles of any kind  - [http://www.tomzavodny.cz/program/subtool/](http://www.tomzavodny.cz/program/subtool/)

---

### Post by CarpKing on 2009-02-07
> **tubunu said:**
> Not true. If you use Devede, you can add subtitles to an avi file and turn them on/off as you wish.

I think that just puts them into a DVD-type file structure, though.  In other words, you convert an avi file and an srt file into mpeg2(?) and whatever subtitle format DVDs use.

For editing subtitles, there's always Gedit ;)

---

### Post by MeTylerDurden on 2009-02-20
everyone says 'use devede' for subtitles/   can someone give a tutorial and explain because there is frickin 50 different encoding choices.. this is insane.  easy to drag and drop but what next..   does anyone explain what encoding is and how to use it.. thank you

---

### Post by Bachstelze on 2009-02-20
> **tubunu said:**
> Not true. If you use Devede, you can add subtitles to an avi file and turn them on/off as you wish.

Do not do this. Softsubs in AVI are not an official feature of the container but more like a dirty hack. Not every player will be able to read them.

@OP: as was said earlier, Avidemux is the easiest way to burn your subs on the video. For editing, you don't need something as fancy as Aegisub if you're only working with SRT subtitles, a simple text editor will do.

---

### Post by MeTylerDurden on 2009-02-20
your answer just blows sunshine up a""    your just pointing a problem in another direction.. does anyone have a logical actually done this answer...  with a tutorial on how is done..

---

### Post by Bachstelze on 2009-02-20
> **MeTylerDurden said:**
> your answer just blows sunshine up a""    your just pointing a problem in another direction.. does anyone have a logical actually done this answer...  with a tutorial on how is done..

I answered the OP's questions. If you need help about something, please create your own thread to ask for it. Asking for help in someone else's thread is not acceptable.

---

