---
title: "How to limit draggable region for application windows like GNOME Panel"
date: 2009-03-12
forum: Programming Talk
---

### Post by C-- on 2009-03-12
Hi, I am developing a Java application for use in GNOME and maybe KDE that requires a persistent view at the top of the screen that a user cannot resize, move, or destroy. However, I am having issues in that a user can drag a window up behind the view, or maximize a window such that the title bar is behind this view, which means that the window's titlebar is no longer accessible and now the window cannot be moved unless the alt button is pressed.

I would like to know if there is a way to prevent users from dragging windows behind my Java application's view or maximizing a window behind the view, much like how the GNOME Panel behaves. Are there any Java functions or GNOME/Linux OS functions I can call?

---

### Post by slavik on 2009-03-12
you have to do straight X calls afaik.

---

### Post by C-- on 2009-03-13
> **slavik said:**
> you have to do straight X calls afaik.

I see, thank you. Would anyone happen to know the location of related documentation?

---

### Post by rg4w on 2010-10-14
> **C-- said:**
> I see, thank you. Would anyone happen to know the location of related documentation?

I would be grateful if someone could share where I could find that as well, as I'm facing a similar challenge and the folks on my team haven't yet turned up the API for this.

TIA -

---

