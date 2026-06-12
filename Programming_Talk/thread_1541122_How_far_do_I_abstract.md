---
title: "How far do I abstract?"
date: 2010-07-28
forum: Programming Talk
---

### Post by Asday on 2010-07-28
So let's say I'm writing a game engine around PyGame.  A little specific for a hypothetical situation?  Well, it's what I'd like to do.  Seems fun.

A major stumbling block I come up against whenever I start planning it in my mind is how far do I abstract things?  Do I just want to write a wrapper(?) for the PyGame library, that makes drawing surfaces more easy, and some sort of windowing emulation maybe, or do I go further, and implement something that deals with all the tiles and collisions, and scripts (for tile-based, etc.)?

I keep coming back to the idea I could write it all in a layered fashion, so the tile-based engine requires the windowing engine, which requires the easy drawing engine, which requires Pygame, but this means when I come to write a platformer engine, instead, (for example), I may need to slightly tweak the windowing engine, which completely breaks the tile-based engine.

(As a side-note, I've always been TERRIBLE at encapsulation.  As an example, [*here's*](http://www.mediafire.com/file/6gj0d10d1dol85c/scrolldem000.exe) a small piece I wrote recently.  Any suggestions on how to practice better practices would be greatly appreciated.)

---

### Post by splicerr on 2010-07-28
> **Asday said:**
> (As a side-note, I've always been TERRIBLE at encapsulation.  As an example, [*here's*]("http://www.mediafire.com/file/6gj0d10d1dol85c/scrolldem000.exe") a small piece I wrote recently.  Any suggestions on how to practice better practices would be greatly appreciated.)

A link to an .exe file. I wonder how many people are actually going to download and run it. Be it  under Windows or Wine. I certainly don't have a habit in downloading and running untrusted binary code.

---

### Post by Asday on 2010-07-28
> **splicerr said:**
> A link to an .exe file. I wonder how many people are actually going to download and run it. Be it  under Windows or Wine. I certainly don't have a habit in downloading and running untrusted binary code.

Thanks for pointing that out, that was completely the wrong link.

[Better link.](http://www.mediafire.com/file/agbktaqfb3czp7z/scrolldem000.rar)

(The .exe was a self-extracting archive for the idorts I was writing for who didn't trust a program that wasn't a .exe.)

---

