---
title: "X11 question"
date: 2008-02-27
forum: Programming Talk
---

### Post by ninjarat on 2008-02-27
So, I have a nice little X11 window set with an OpenGL context in it, and it just works peachy.  I set up a dispatch events loop which works fine.  But when I hit Alt-F4, instead of letting me handle it all myself, it interrupts my shutdown procedure and just quits.  How can I stop it from doing that?  Is there some way to tell it I'll handle that myself?  Thanks.:confused:

---

### Post by ninjarat on 2008-02-27
Never mind.  I got it.  I found out that it was being killed by the WM_DELETE_WINDOW protocol atom, so I intercepted that.  Man, I didn't find that anywhere.  Has someone else had that same problem?  Because I have source code to share if so.

---

