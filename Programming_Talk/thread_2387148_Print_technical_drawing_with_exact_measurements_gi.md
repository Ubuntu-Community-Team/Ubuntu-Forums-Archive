---
title: "Print technical drawing with exact measurements given a list of segments"
date: 2018-03-15
forum: Programming Talk
---

### Post by Arndt on 2018-03-15
I asked this on stackoverflow, and they didn't seem to like it, so I try here. Maybe Programming Talk is wrong, but I don't know what is right. To me, this is general programming/development, even if the answer is not new program code.
-------------


What I want to do is to make a technical drawing of my apartment (in 2d), with walls, doors, electrical sockets etc. Since I didn't need any advanced drawing, I wrote a simple program which, given my measurements which I entered, produces a list of segments, each segment represented by two points, whose x and y coordinates are given in meters.

So far, I am content with this - I can generate svg for example, or input the list to a program which displays the drawing on the screen.

My problem is in accurate print. I want the measurements in meters to correspond exactly to centimeters on the paper (or some other nice scale, like 1:200) and I want to be able to use the whole sheet. After experimenting a little with my generated svg in Firefox, I did get the right scale, but found that the drawing is clipped in order to show header and footer. Deselecting header and footer doesn't remove the clipping.

The simplest program which would satisfy my need would be a non-interactive one which converts my segment list to the appropriate Postscript or PDF code.

Alternatively, one of the freely available CAD tools might import the segment list (perhaps after some formatting) and print the way I want.

If I find nothing else, I will write such a tool myself and generate Postscript, but maybe someone has already solved the problem.

What do you suggest?

---

### Post by TheFu on 2018-03-15
libreoffice draw?

Or do you want to do it with your own code?

---

### Post by Arndt on 2018-03-16
Do you know for sure that libreoffice does this?

I don't want to do it with my own code unless I have to, as I wrote.

---

### Post by TheFu on 2018-03-16
Libreoffice doesn't. LibreOffice-Draw ... is a MS-Visio replacement. So ... er ... yeah.

---

### Post by SeijiSensei on 2018-03-17
Have you tried opening and printing it from the [GIMP]("http://www.gimp.org/")?  You should be able to manipulate the picture with GIMP to your heart's content.

---

