---
title: "Screen-mate"
date: 2009-03-19
forum: Programming Talk
---

### Post by Xyem on 2009-03-19
I'm looking to make a "screen mate" type of application where a 3D model is drawn on top of all other windows and input like mouse clicks "pass through".

Initially, I was attempting to use the Shape extension with my OpenGL window but it wasn't fast enough and causes the window to flicker.

My other thought would be to render the image off-screen and then display the image on the desktop ( using solid green as transparent for example ).

I'm a little stumped on how I would achieve this though. Are X11 overlays what I am looking for or could someone point me to a similar project where I could get some inspiration?

---

### Post by slavik on 2009-03-19
Clippy has finally come to Linux?

---

### Post by Xyem on 2009-03-20
No.

Just... no.

:P

---

### Post by Xyem on 2009-04-09
Bump

---

### Post by Firestom on 2009-04-09
What do you mean by screen-mate? Any example of what you're telling us? Because it wouldn't be too hard, especially if you think about using the toolbar to do so. In the toolbar would be perfect, you should just have to look how to embed applications into these.

---

### Post by Xyem on 2009-04-09
Perhaps you will remember [SCMPOO](http://www.geocities.com/SiliconValley/Way/9096/index2.htm) ( Stray Sheep )
I have seen one for Linux where the default is a penguin but you can download other "skins" but the name escapes me now. Also, Bonzi Buddy was pretty well known example.

I don't want it limited to the toolbar, I want it to be able to be anywhere on the screen. The main difference between those examples and what I want is they are all sprite-based whereas mine will be an OpenGL rendering and it doesn't have to be interactive ( in fact, I'd prefer it not to be ).

---

