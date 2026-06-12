---
title: "Newbie question about C and GTK programming."
date: 2009-04-13
forum: Programming Talk
---

### Post by riskbreaker927 on 2009-04-13
I'm taking a C programming course at my university. For my final  I have to write a program that will parse a text-based maze and display the solution to it. That much is easy, so for extra credit I've opted to create a GTK UI for the program. I want to be able to display the maze within the window.

I plan to do this by reading the maze (using fscanf) into a two dimensional array, with each member being either a space or a wall, then using two nested for loops to generate the widgets for each array member into a table. My question is: would this work? Can you use for loops to draw GTK widgets?

---

### Post by simeon87 on 2009-04-13
Yes. Not sure why you need a widget for each location in the maze though.. a maze can also be drawn on a GtkDrawingArea.

---

### Post by riskbreaker927 on 2009-04-13
I haven't read enough about GTK yet to know what drawingarea is, but I'll look into that.

---

