---
title: "GUI and graphics programming"
date: 2009-03-20
forum: Programming Talk
---

### Post by monguin61 on 2009-03-20
I want to write a basic GUI-based application that has access to a drawing area or drawing window of some sort. I've been looking around, and I think I'll be happy with gtk for the GUI, but I'm having some trouble making up my mind for the graphics library. Theres openGL, SDL, cairo, and probably others. I assume these have their respective strengths and weaknesses, and that each is appropriate for only certain things - are any of them really slow and bloated, harder to use, etc? I mostly just want a simple blank canvas widget within a window, with the freedom to draw whatever I want, using the full speed of C)

Any help is appreciated.

---

### Post by hessiess on 2009-03-20
Dusen't GTK have a bitmap drawing widget?, must have because it was made for GIMP.
SDL is resolution dependent, implemented mostly in softwere(can be slow) and lacks basic things like rotation and scaling.

---

### Post by jimi_hendrix on 2009-03-20
hessiess has a resolution independent engine like SDL

opengl is more complex but its the API if you want graphics i think

---

### Post by simeon87 on 2009-03-20
Using Gtk with cairo would work fine: Gtk has a DrawingArea widget which you can draw on using cairo.

---

### Post by mmix on 2009-03-21
SDL seems to be the right tool for you.

---

