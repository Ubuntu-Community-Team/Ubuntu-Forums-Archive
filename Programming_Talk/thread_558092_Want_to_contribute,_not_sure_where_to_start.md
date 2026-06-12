---
title: "Want to contribute, not sure where to start"
date: 2007-09-23
forum: Programming Talk
---

### Post by mb108 on 2007-09-23
Posting here cause I've been using Ubuntu for a couple of years now, and have gotten a lot out of the great community resources. I've become a strong believer in open source, and I'm looking for a way to contribute.

Some backstory: started programming very early (10 yrs old), kept taking classes through college, getting a CS minor. Exposed to everything from BASIC to Java, with even some asm and Lisp for flavor... but on what I would consider a very amateur level. So I'd say I have a strong "knack" for code, but lack the depth of experience that comes from working on a real project. And I've been out of the habit for a few years now, so kind of rusty (although I wrote my first bash script the other day -- simple, practically a one-liner, but it felt good).

So the hidden motivation is that I miss coding and would like to be involved in a project that will keep me "in the habit."

Did some searching on how to get started in open source, and the main advice seems to be "scratch your own itch." The main thing that itches right now is that there's no interface for [_this toy_]("http://www.automatedoutlet.com/product.php?productid=1248")... but a device driver/interface might be over my head (or maybe not, I have no idea). I've searched for an existing project working on this, but the closest I can find is a company selling a .NET SDK bundled with it. Neil Cherry over at linuxha.com has also noted the lack of interface for this device, maybe I should contact him?

I'm somewhat of a gamer (not sure I want to work on a game though), and I'm interested in some of the embedded projects (eg OpenMoko). But mainly, I'm itching to write some code, and learn more about how things work.

Some random questions:

Any advice on where to get started? (or even a better place to ask this question?)
Any must-read material for someone with my experience profile? (CVS and Makefies are 2 topics I already feel I need to learn more about)
Any recommendations for classes (online or in the Los Angeles, CA area)?
Is there a place to find people interested in mentoring?
Is there a project you know of that wouldn't mind a newb with some knack poking around? (and how to do so without becoming a nuisance?)

Thanks for any advice on this, I realize it's a lot of questions -- feel free to respond to as little or as much as you care to.

---

### Post by aysiu on 2007-09-23
This may be a good place to start:
[http://www.ubuntu.com/community/participate/developerzone](http://www.ubuntu.com/community/participate/developerzone)

---

### Post by mb108 on 2007-09-23
> **aysiu said:**
> This may be a good place to start:
[http://www.ubuntu.com/community/participate/developerzone](http://www.ubuntu.com/community/participate/developerzone)

Haha... erm... I had a feeling I was overlooking something obvious. Thanks, I don't know how I missed that.

Since I posted I also found the OpenEmbedded docs, and things are chugging away in the background setting up for that. So I will soon have a "Hello, world!" on my internet tabl... oh wait, I don't have one. :lolflag: ...adding qemu to the list of things to install....

---

### Post by pmasiar on 2007-09-23
> **mb108 said:**
> I'm somewhat of a gamer ... and I'm interested in some of the embedded projects (eg OpenMoko)....

It all depends what language you will decide to go for. I would recommend Python: It is simple to learn, and forgiving if you don't have time to hack for couple of months: some languages are unforgiving in this sense (Perl, Java), you will forgot many quirks and get confused, but not in Python.

If you use Python, you don't need makefiles, and CVS is obsolete anyway, use Subversion instead, with excellent GUI front-end: pysnv workbench.

Pygame might be good place to start.

But to really start, don't bother with GUI first: write text based commandline programs. Wiki inmy sig has many links, I recommend pythonchallenge: 33 levels of puzzles, solving each one will teach you part of Python. With forums for every level (with hints).

> 
Any recommendations for classes (online or in the Los Angeles, CA area)?
Is there a place to find people interested in mentoring?

I am not sure if classes are right for self-learner: by yourself, you can go where you fancy at your own speed. but if you think you need guide, O'Reilly has online certification classes, they look good, and you have 7 days money back guarantee if you don't like it.

> 
Is there a project you know of that wouldn't mind a newb with some knack poking around? (and how to do so without becoming a nuisance?).

Every project likes to get new developers: whole trick is to show you are self-learner, can google before asking, and can follow advice.

Python has mailing list "Tutor" for python learners.

My personal hobby project is to create open-source clone of [http://en.wikipedia.org/wiki/Game_maker](http://en.wikipedia.org/wiki/Game_maker) , excellent GUI to introduce kids to programming without writing any code. If you are interested, PM me.

---

