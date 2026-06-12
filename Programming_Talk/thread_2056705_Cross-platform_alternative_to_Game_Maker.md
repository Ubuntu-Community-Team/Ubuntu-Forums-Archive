---
title: "Cross-platform alternative to Game Maker"
date: 2012-09-12
forum: Programming Talk
---

### Post by mode7 on 2012-09-12
Hello all.

I wrote a super long (Yes, more than this one) post explaining my frustrations and exact needs, but I felt I'd erase it and get to the point.

Situation: After using GM for several years, I have had it with GM and YYG (Parent company). The lack of cross-platform support, bugginess, constantly increasing price, and bad user support have driven me insane.

While I have attempted to get into other languages and libraries for quite some time now, I simply cannot get anything to tie together into a full-featured engine for the life of me.
I am fine with smaller-scale scripting and design. All my projects are written using scripts and "Execute Code" actions, and I have designed the back-ends for several games my friend and I have put out there.

It seems that when I try something else, for instance C++ and SDL, I can get the individual components to work. An object that will draw itself, transform itself, respond to input, make sounds, etc. 
I cannot get everything to come together, though. A centralized system for receiving input, something to manage sprites and objects, a system for GM's "Views".

I need to break away from GM, and the obvious bad habits it is getting into me.


Requirements) So.. are there any Linux refugees from GM that can tell me how they transitioned into a C++/Java/ETC environment for game design? What libraries they used?
I need something cross-platform (Or at least Windows and Linux, OSX is a plus).. so Mono and Java would be great. I do know C/C++ basics too. I know everyone recommends PyGame.. but I cannot get into Python at all (But am willing to give it another try).

If anyone knows any good resources to read up on, I'd appreciate it. While I can find tons of "2D game development tutorials", I can't find anything that will go over a scalable ENGINE to design my own concepts on.

I appreciate any help, and if I can be more specific or whatever, just let me know. Thanks!

---

### Post by juancarlospaco on 2012-09-12
**[http://www.pilas-engine.com.ar](http://www.pilas-engine.com.ar)**

---

### Post by Sslaxx on 2012-09-12
For a few:
[http://www.stencyl.com/](http://www.stencyl.com/) - Stencyl. Not sure how much good this is, but it claims to support iOS, Flash and eventually HTML 5. MMF clone more than Game Maker though.
[http://www.en.compilgames.net/](http://www.en.compilgames.net/) - another MMF-type.
[http://game-editor.com/Main_Page](http://game-editor.com/Main_Page) - a bit more low-level than the other two I've mentioned.

---

### Post by mode7 on 2012-09-13
Thanks!
@Juan, looks nice, but everything (Including the functions) are in Spanish :( I could work around that.. but I might as well use an English API.

@Sslaxx, nice suggestions. I forgot about Stencyl. The upcoming 3.0 supports html5, which I like. Never heard of Game develop, but will try it. Game editor looks less maintained, but will try it for sure.

I didn't mean it had to have an editor like GM, more or less a similar feature set, but nonetheless appreciated. I will try those products tonight at work ;)
What I'm really looking to find is a breakthrough from GM into lower-level (or not), reliable, cross-platform solutions. Java, Mono, C++, with SDL, Clanlib, Allegro, etc. I suppose I just need to keep blundering around before I finally understand something.

---

