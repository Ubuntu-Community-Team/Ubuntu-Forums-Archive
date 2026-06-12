---
title: "Linux &amp; Memory Editors for Game Cheating"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by orbitaldecay on 2008-11-20
On the Windows platform there are many memory editors and trainers available to assist with game cheating, tweaking, etc. (Cheat Engine, for example).  I have been searching for similar software for *nix and I have been unable to find any.  I have read in some places that it is not possible to write such a program for *nix.  Does anyone know more about this?  Wouldn't it be possible to create such a program in linux using ptrace()?  Thanks! :)

---

### Post by LowSky on 2008-11-20
you can try to run some of those progrmas you mentioned with WINE

---

### Post by orbitaldecay on 2008-11-27
For anyone else who's trying to track down an answer to this question; you can't pull it off within wine :( There is a linux port of Cheat Engine.  I haven't looked at it, but it's available at [http://cheatengine.org/index.php](http://cheatengine.org/index.php).  Just read through the first post.

I have also seen a lot of recommendations for GDB.  GDB doesn't support sufficient search features for this kind of thing.  If all you want to do is Cheat Engine / Tsearch style game hacking, I don't recommend GDB.  Now if you are looking for a wicked debugger, that's another story ;)

I've also read some posts from various folks suggesting that it isn't possible to write a universal trainer for Linux.  Do not be misled, this is untrue.  There hasn't been much development in this area, but it's very possible (easier to do in Linux than in Windows imho).

---

