---
title: "How should I make my game extendable?"
date: 2009-06-13
forum: Programming Talk
---

### Post by Nuticulus on 2009-06-13
Hi,

I am currently programming a game "collection", i.e. you have a menu and you can choose one of several minigames to play. I want to have the minigames stored as separate files, so that they could be downloaded and installed, for example, or modified, without needing to recompile the main source code. This would mean that the main executable would have to interpret the game files somehow.

Does anyone have any suggestions on how I should implement this? I would prefer it if the file was parsed when the game was first opened, and then not used while the game was played.

Thanks...

---

### Post by JordyD on 2009-06-13
> **Nuticulus said:**
> Hi,

I am currently programming a game "collection", i.e. you have a menu and you can choose one of several minigames to play. I want to have the minigames stored as separate files, so that they could be downloaded and installed, for example, or modified, without needing to recompile the main source code. This would mean that the main executable would have to interpret the game files somehow.

Does anyone have any suggestions on how I should implement this? I would prefer it if the file was parsed when the game was first opened, and then not used while the game was played.

Thanks...

Instead of parsing them, could you not make them executable? Make the main program provide an API which can be coded for, then code all your games for that API. Make you main program list the directory contents for a list of games and playing the game would simply execute it.

---

### Post by Nuticulus on 2009-06-13
Do you mean that a game would run "within" the main program? I'm not sure how to implement this - I'm using c++.

---

### Post by soltanis on 2009-06-13
I believe what he's saying is separate your game into an engine (which performs rendering, indexes entities, performs logic, outputs sound and does other stuff) with the actual game logic (which would specify which resources to load, when to use them, and how the game actually works).

These don't even have to be the same binary images (i.e. your engine could be an executable that loads a shared library, or the other way around).

This is how Quake, Half-life, and most games which follow that line implement extensions (mods).

EDIT.

Or implement a scripting language for extenders to code in. One very common one is Lua, but Perl, Javascript, and others are also embeddable.

---

### Post by Nuticulus on 2009-06-14
Thanks! I have now got basic Lua support - got a lua file to draw an image. Thanks for your help! This is exactly what I was hoping for.:D

---

### Post by nvteighen on 2009-06-14
Just for your interest, look at my sig and you may take some ideas from my PycTacToe project. Yes, it's Python, so it makes this kind if job much easier being an interpreted language, but the basics of its plugin API design should be transferrable into C++ (and any language).

FreeTruco (in Scheme) is also extendable, but with an absolutely experimental approach... :p Basically, it's a new Lisp-dialect that uses the Scheme interpreter as its own interpreter... (talk about recursion!)

---

