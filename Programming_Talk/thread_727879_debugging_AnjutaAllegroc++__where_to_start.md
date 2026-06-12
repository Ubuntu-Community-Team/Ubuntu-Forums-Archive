---
title: "debugging Anjuta/Allegro/c++  where to start?"
date: 2008-03-18
forum: Programming Talk
---

### Post by mordi05 on 2008-03-18
Hi.
I created a basic poker game with c++/anjuta using the Allegro library. The program has some issues.

When I loop the poker game to play consecutive games, It will abort after a while with the following error:
(Shutting down Allegro due to signal #11)
This can happen after 2-5 poker hands. And sometimes even before the first one. Because the code, at least sometimes,  works for a while I suspect it may be some memory problem. 

I am several times during the code loading new images into my basic bitmaps (11 bitmaps total). And then drawing them to the screen over the old ones. Maybe this is a stupid thing to do. I don't know :-)

However I am quite new to programming and have no debugging experience. I tried running the anjuta debugger, but I am sad to say it is cryptic to me.

I realize that the problem is impossible to identify from this info, but maybe someone could point me in the right direction as to begin debugging. Or understanding the debugger.

---

### Post by mordi05 on 2008-03-18
Sorry to double post, but if there is a way to use the debugger to trace exactly where my program aborted I could maybe find the error.

Or some other way to trace this. The problem is that since my program runs in fullscreen mode the debugger locks up when the program get to the fullscreen part. Even though this is working when not run through the debugger.

---

