---
title: "OpenLieroX search for devs and beta testers"
date: 2009-10-13
forum: Programming Talk
---

### Post by albertz on 2009-10-13
Heya there,

First, about the game: [http://openlierox.net](http://openlierox.net)
Just try it out if you want to know if that is an interesting game for you.

We are a small team (3 main devs, all of us busy with job or study) with an old (>10 years) and medium sized (~300k loc) source code base (mostly C++) which has become more and more clean over the time (not perfect but I often wonder myself how straightforward most things are and that it mostly just works out-of-the-box when you try something new). We don't have very strict rules, we often try out new things (which works great as everybody still has some sort of sense of responsibility for the team - and you can anyway just redo anything in a Svn/Git) and we have a good communication with each other.

Now, if you would like to contribute, you can basically do what you want, you are in any case welcome.

What we search most:

* Beta testers with some extra knowledge (for example to handle a coredump and/or to use GDB).

We really miss those people yet. Most of our players have too less experience to do that; most of them are also on Windows.

Also, some more exotic architectures would be nice. I had a PPC myself earlier so the code is endian independent and also works the same way for 32/64 bit, so it really should work almost everywhere. But I don't have that system anymore and it would be nice to get some feedback with users of more exotic systems.

* Core developers. Well, hard to find somehow. Of course you have to get known to the whole codebase. But that is not a big problem with some time - after a day you can do most things and after a week you should have a very good overview.

Btw., C++ knowledge will of course make it a lot easier for you but it might also be interesting for beginners. There are many tasks where a beginner could start and get some nice results very fast (for example writing a gamemode or making some smaller improvements/additions here and there). Also one of our main devs started to code C++ with this project. And the other one was ready within a few days to contribute a lot to the project.

Anyway, some of the upcoming bigger tasks are: 

New net engine. Right now, client/server functions are kind of mixed. For example, the projectile simulation and the worm movement is calculated client side (initially to give a more fluent feeling). This has many disadvantages though. We basically want to move away from that to have everything serverside. This is not really simple (it earlier didn't seemed possible at all) because we have really a lot of projectiles (around 3000) and the speed of the worms is often very high and it is really important that all reactions are handled in kind almost realtime.

Better graphics engine, based on OpenGL. Right now, most things are done with direct pixel manipulation, mixed with some alpha blending here and there which is all done in software, which makes it kind of slow.

New physics and gamescripting, also more dynamic levels with scriptable elements, all based on Lua. We are planning to adopt some code of the Gusanos project here (if you know of it).

* Python developer for Dedicated server script

Our dedicated server has become useable and mostly stable. Though, the current dedicated script lacks some features. It currently has some simple for of voting implemented but this should be extended. Also the map / mod rotation is kind of simple and stupid at the moment. And the automatic switching from DM to TDM (or to other game modes like CTF, Hide&Seek, Race, or whatever) also is stupid and often annoying in game.

Also, the dedicated server needs more testing and more people who uses it. Some quite rare bugs in OLX only appear in the dedicated server, sometimes even only after some weeks of runtime. I frequently try to debug them myself, but it just takes some time to find them. Whereby my last run was fine for over 5 weeks, when I finally had to reboot the system.

* Helpers for this and that. There are so many things which need to be done. This is to manage the bug trackers, to manage/test/package/build the releases, to arrange things in the community (asking for further help).

For example, we like to have some more ingame sounds, something like "3 frags left" and a lot of similar things, perhaps also some sounds/voices for the worms itself (well, you can think that further). Somebody would have to collect all sounds from the users, convert them to a common format, make them all the same volume, fix the length and such stuff. I already have some of them on my computer (we actually asked the community already to help us here) but they are completly random, all the volumes are a bit different and also the quality differs a lot (so some of them should be redone) and so on. I sadly didn't had the time yet to ask for further updates / more sounds. But it would be really nice to see such thing finally in the game.

Also some easier coding tasks would be nice. For example, we like to include Googles Breakpad (that is a crash handler, the same is also used by Firefox, to send crash reports to the Firefox bug database) and to setup the backend server which can handle such crashreports. Such system would make the debugging much easier because we probably would get much more crash reports.

The design team of OpenLieroX also needs some more help. For example, a new GUI system was planned a long time ago, and with it a new layout of all the game menu. Esp. the options dialog seems kind of a challenge (whereby I already like the current solution somehow, at least the idea to have a slider to set the advanced level of details of the game options; not perfect yet but better as in the past).

---

Well, so far from me. Perhaps just contact us or take a look at the community ([http://www.openlierox.net/forum/](http://www.openlierox.net/forum/)).

---

