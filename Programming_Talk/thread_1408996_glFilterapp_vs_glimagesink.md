---
title: "glFilterapp vs glimagesink"
date: 2010-02-17
forum: Programming Talk
---

### Post by Eirel on 2010-02-17
Does anyone ever try to use glfilterapp by redefining its client draw callback function? Actually, I've written a little application using glimagesink, but have to change it to record it in a file instead of display it. That's why I want to use glfilterapp in place of glimagesink. But if my callback works for glimagesink, it doesn't when I use filterapp. i've got no texture, no stencil buffer etc...
Does anyone have an idea about it?

---

### Post by Eirel on 2010-02-17
A first improvement: there was a mistake in the drawing callback declaration. Actually, if I correct it (i mean argument must be width, height, texture, data, and no more texture, width, height, data like in the glimagesink's one), I've got the video texture which come back. But still no stencil buffer, and that's what did all the attractive part of my application...
If anyone has a single idea...

ps: sorry for all mistakes I can do, I'm french...I know, it doesn't excuse everything^^'

---

### Post by Eirel on 2010-02-18
up?!

---

