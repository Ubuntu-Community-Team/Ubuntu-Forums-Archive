---
title: "Gweled Bot: Closing Game Over window"
date: 2012-07-26
forum: Programming Talk
---

### Post by InkyDinky on 2012-07-26
I've written a Gweled bot that plays the game for me. Currently I have to manually click the "New Game" button on the Game Over window. I'd like to automate this task for testing purposes of different gameplay algorithms.
My current method uses xwininfo to search for the "has no name" child of the Gweled window. 
```

xwininfo -root -tree | grep Gweled | grep 'has no name'

```
The problem with this method is that the spawned child window still shows up in xwininfo after I click to start a new game.
I believe that the width/height are reported as 1x1 when the game over window has been closed.  I'm fine with going this route, however if there is a better way to go about handling this I'd love to hear about it.

Reading the xwininfo manpage I don't see anything that would help. 
Also if anyone has insight or can point me as to why the gameover window still shows up in xwininfo despite being closed I'd like to understand that better. Is this behavior programmed or part of the window manager?

Thanks!

---

