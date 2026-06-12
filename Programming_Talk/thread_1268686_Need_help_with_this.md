---
title: "Need help with this"
date: 2009-09-17
forum: Programming Talk
---

### Post by nebu on 2009-09-17
Hey I wrote some java code to read a line from a file which contains 4 numbers x0 y0 x1 y1 and consequently plot the line from(x0,y0) to (x1,y1)

there can be multiple lines in the file.....


the problem i am facing is that the only the last line is being drawn on the screen rather than all of them being there.....


i ahve attached the code....



ps... @admins.... u shud allow us to upload java code(ie .java files!)!!

---

### Post by Reiger on 2009-09-17
Without even looking at your code: you are reading the file line by line and then drawing each line individually? :P

'Cos that means you are actually seeing Java having some serious speed: it is in fact drawing everything but only one line will remain visible because the Graphics object is erased on each paint(). 

What you will want to do is use a BufferedImage(width, height, image_type); then draw on the buffered image; and in the paint() method draw the buffered image.

---

### Post by nebu on 2009-09-17
i tried to implement it.... could u just check the code... im still getting the same output

---

