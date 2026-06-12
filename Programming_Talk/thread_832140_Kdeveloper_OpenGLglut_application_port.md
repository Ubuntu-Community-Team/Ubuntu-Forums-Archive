---
title: "Kdeveloper OpenGL/glut application port"
date: 2008-06-17
forum: Programming Talk
---

### Post by Clive McCarthy on 2008-06-17
In Ubuntu/Linux does OpenGL/glut's glutFullScreen() really go full screen (no framing or title bar) as it does on XP? I'm using Kdevelop is it "containing" the OpenGL window as a child? Conversely, when not full screen, my OpenGL window has no title bar so I can't see the results of calls to glutSetWindowTitle() -- is this Kdevelop at work too?

Should I be using glutGameMode() instead of glutFullScreen() ?

I realize these are VERY specific questions about the interactions of Ubuntu/Kdevelop/OpenGL/glut but not so obscure I hope? Maybe I should post this to the Ubuntu gamers?

I have discovered (by using Geany as opposed to horrible Kdevelop) that Linux glutFullScreen() retains the frame & tile bar. I'll have to use glutEnterGameMode(), which doesn't seem to function on Windows XP! XP's version of glutFullScreen() has no frame & title bar, just like GameMode on Linux. The normal trials of porting, I guess. :(

Linux: use glutEnterGameMode() -- and re-register all the callbacks
XP   : use glutFullScreen()    -- no GameMode, but this is equivalent

---

