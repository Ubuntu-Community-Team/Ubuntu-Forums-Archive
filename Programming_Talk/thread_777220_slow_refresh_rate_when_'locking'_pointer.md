---
title: "slow refresh rate when 'locking' pointer"
date: 2008-05-01
forum: Programming Talk
---

### Post by Thormidable on 2008-05-01
I've been writing a game engine in Windows using OpenGL, and producing my own event handlers. I have recently moved to Xubuntu and have been porting my code. I intended to only use the OpenGL and OpenAL Libraries as this was primarily a learning experience. I've built most of my Event Handler, and keys and shell events work. 

However :
         -The mouse seems to produce huge values for pointer speed calculated by taking the distance the pointer has moved each frame)
         -When I try to 'lock' the pointer to the center of the window with XWarpPointer(), My frame rate drops from several hundred to about 60. 

I've searched online, and on the forums. I'm pretty sure I don't have a loop from XWarpPointer to my Eventhandler. I could put up code, if it would help, but I was wondering if there was a simpler or quicker way to allow unlimited mouse movements.

Thanks in advance

---

