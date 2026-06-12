---
title: "X11: Locking event queue?"
date: 2013-01-03
forum: Programming Talk
---

### Post by tarzanman6 on 2013-01-03
Hello everyone,

I'm working on a small fps demo using a game engine called: Gameplay 3D. A few days ago I decided it was time to lock the cursor to the center of the screen so the player could freely look around the map, but when I tried implementing the engine's function it did nothing. I later found out  that the function had only been defined for the windows platform. So, without any prior knowledge of X11, I decided to carry the burden of defining this function.

So far I've been able to warp the cursor to the center of the screen and turn it invisible. In order to keep the mouse in the center of the screen I called XWarpPointer inside the event cycle, but when I run the application and move the cursor around the screen it "vibrates" as it moves. It seems the XWarpPointer function adds a "mouse moved" event into the queue. **So my question: How can I lock the x11 event queue before calling XWarpPointer so the cursor can move to the center of the screen without adding a "mouse moved" event to the queue? Or is there some other way of resolving this problem?**

_Link to..._
...Gameplay 3D's main page: [__click__]("http://gameplay3d.org/")
...post where I added the code I created (The relevant code is on the 8th post entry by (username) Aluthreney, that's me :D): [__click__]("http://www.gameplay3d.org/forums/viewtopic.php?f=3&t=241&sid=d5ce5e2f8046ab1f46bc63de42420720")

Cheers,
Tarzanman6

---

