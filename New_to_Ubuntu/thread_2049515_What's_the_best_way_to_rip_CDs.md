---
title: "What's the best way to rip CDs?"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Raphicerus on 2012-08-28
This has been triggered off by "What music player to use?" which I was just reading.

I hardly ever listen on the computer, but use it to rip my CD collection, to listen to on MP3 players.

I used to rip CDs with MS Multimedia Player. Not very flexible, but it usually  found the  track information.

I ripped one recently with RhythmBox, and it abjectly failed to find the CD metadata on the Web (though to be fair it was an audio book, so not exactly mainstream).

Now I'm looking at things with new eyes, I wondered if I should even be trying to use a "music *player*" for ripping. From my Ubuntu experience so far, I wonder if there are programs that do nothing _but_ rip CDs perfectly, with a huge range of options.

What do you recommend?

---

### Post by edeneen on 2012-08-28
xfburn

---

### Post by Cheesemill on 2012-08-28
I use abcde.

It's a command line tool but it's easy enough to set up how you want, you just need to edit the well documented abcde.conf file.

I've got it set up to look up the track information, and then encode into flac files which are saved in the correct folder structure in my Music folder. All I have to do is open a terminal and type:
```
abcde
```

In case you're wondering why I don't use a graphical application, I don't have an optical drive in my workstation. All of my encoding is done on my headless fileserver, I just ssh over and run the command.

---

### Post by Cheesemill on 2012-08-28
> **edeneen said:**
> xfburn
Isn't xfburn just for burning CD's?

---

### Post by mansonfan78 on 2012-08-28
I find Grip works pretty well, takes some getting used to, but does just about everything you need it to.   You can find it in the software center.

---

### Post by edeneen on 2012-08-28
> **Cheesemill said:**
> Isn't xfburn just for burning CD's?

no,  Xfburn is a simple CD/DVD burning tool based on [libburnia libraries]("http://www.libburnia-project.org").  It can blank CD/DVD(-RW)s, burn and create iso images, audio CDs, as  well as burn personal compositions of data to either CD or DVD. It Is  stable, and under ongoing development.

from;  [http://goodies.xfce.org/projects/applications/xfburn](http://goodies.xfce.org/projects/applications/xfburn)

---

### Post by oldfred on 2012-08-29
I have not done it for a while, but I use Sound Juicer to extract to flac and Sound Converter to write as MP3. For whatever reason it seems to convert & write to my MP3 player faster then just copying the MP3s, if previously converted.

---

### Post by 2F4U on 2012-08-29
I am using abcde.

---

### Post by Cheesemill on 2012-08-29
> **edeneen said:**
> no,  Xfburn is a simple CD/DVD burning tool based on [libburnia libraries]("http://www.libburnia-project.org").  It can blank CD/DVD(-RW)s, burn and create iso images, audio CDs, as  well as burn personal compositions of data to either CD or DVD. It Is  stable, and under ongoing development.

from;  [http://goodies.xfce.org/projects/applications/xfburn](http://goodies.xfce.org/projects/applications/xfburn)
So as I said, it's just for burning CD's.
You can't use it to rip audio from CD's.

---

### Post by fooman on 2012-08-29
i use k3b.

---

### Post by Raphicerus on 2012-08-29
I installed abcde, and it picked up the CD information, no problem.
Simple to configure and use, and it does good VBR encoding via Lame.

Thanks for the ideas. Another one solved!

---

### Post by suso on 2012-10-15
> **mansonfan78 said:**
> I find Grip works pretty well, takes some getting used to, but does just about everything you need it to.   **You can find it in the software center.**

No its not in apt or the software center anymore, unless you have some 3rd party source in your apt or something. Grip is unfortunately no longer distributed through normal Ubuntu repositories. I think this has been the case for a few years now.

---

### Post by andrew.46 on 2012-11-10
> **Raphicerus said:**
> I installed abcde, and it picked up the CD information, no problem.
Simple to configure and use, and it does good VBR encoding via Lame.

Perhaps have a look at an old page of mine for a guide to getting a decent config file:

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

In an interesting development newer versions of abcde will be using *eyed3 *to write the mp3 tags. This is not reflected in the page above but will be soon...

---

### Post by Raphicerus on 2012-11-11
> **andrew.46 said:**
> Perhaps have a look at an old page of mine for a guide to getting a decent config file:

[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

In an interesting development newer versions of abcde will be using *eyed3 *to write the mp3 tags. This is not reflected in the page above but will be soon...

I've bookmarked that page - thanks, Andrew. The configuration probably does need some fine tuning.

---

