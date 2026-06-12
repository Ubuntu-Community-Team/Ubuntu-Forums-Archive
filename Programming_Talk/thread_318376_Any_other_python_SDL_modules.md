---
title: "Any other python SDL modules?"
date: 2006-12-13
forum: Programming Talk
---

### Post by Wybiral on 2006-12-13
I've been looking for a python module, other than pyGames, that wraps SDL into python. So far I haven't found any. If there isn't one, I will probably make one. I'm looking for something with just SDL, and some of it's extensions like SDL_image. Thanks.

---

### Post by po0f on 2006-12-14
Wybiral,

Can you not use [python-imaging](http://packages.ubuntu.com/edgy/python/python-imaging) with pygame?  Don't beat me up if it's a "no", I never tried it.  (My gut tells me "no" but it's an idea.)  :)

---

### Post by Wybiral on 2006-12-14
I want something more direct to SDL, pyGame doesn't seem to be as direct in terms of the syntax, but maybe I just haven't looked into it enough. I wonder why there isn't just an SDL for python?

---

### Post by po0f on 2006-12-14
Wybiral,

So is your beef with pygame is that it isn't low-level enough?  What exactly are the differences between Python/Pygame and C(++)/SDL?

---

### Post by Wybiral on 2006-12-14
Its mostly the syntax, it seems very different. Using straight SDL commands would be cleaner and easier. I am very tempted to write my own module (it's not hard to wrap a pre existing library) but if there is one out there... Then that would be even easier!

---

### Post by &lt;mawe&gt; on 2006-12-14
Hi!

Maybe [PySDL](http://pysdl.sourceforge.net/) is what you want? I haven't done anything with it yet, just found it via google. 

Regards, mawe

---

### Post by Wybiral on 2006-12-14
That one does look alot closer to the SDL syntax, thanks!

---

### Post by po0f on 2006-12-14
Wybiral,

If you didn't notice, most of the links on that page are 404s.  They link to the wrong SDL homepage, and the SourceForge downloads page has somewhere in 2000 as the upload time on the one, solitary download available.  Just to give you a heads up.  :)

---

### Post by Wybiral on 2006-12-14
I managed to download it from the sourceforge site.

I do wonder... Why isn't there a kept-up SDL module for python? Seeing how SDL is one of the most commonly used libraries for linux game developers (mostly), and python is such a hot language... I would think an SDL module would be almost mandatory.

---

### Post by pmasiar on 2006-12-14
> **Wybiral said:**
> I do wonder... Why isn't there a kept-up SDL module for python? 

Let me think aloud **what I would do if I was in business writing (commercial proprietary) games in python**: If SDL is (1) easy to wrap, and (2) I am the only obvious company doing games in python now and incurring all development costs: I would consider having my *own proprietary python wrapper around SDL* - as my competitive advantage. Let other companies write games in C++ and SDL, I *could* prefer to maintain (simple) python bindings to SDL and not giving competition idea how easy is to increase productivity by switching to python.

And obviously when writing games in python, I am prepared to move some 5% of my "critical path" code from python to C anytime, so mixing python and C inevitably is my core competency. IANAL, but IMHO python licence allows to make proprietary libraries like that.

In this situation, releasing SDL wrapper will not help me, but the competition, so I am *not* going to release it. YMMV.

---

### Post by Wybiral on 2006-12-14
Yeah, I can see how that would happen... But why hasn't the open source community done anything about it? Python is a very commonly used open source language and SDL is a common open source library... Maybe sometime soon when some of my projects die down a little I'll write a syntax correct wrapper for SDL in python.

---

