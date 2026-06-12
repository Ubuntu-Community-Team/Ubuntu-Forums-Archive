---
title: "Printing a canvas in python"
date: 2010-05-31
forum: Programming Talk
---

### Post by japhyr on 2010-05-31
Hello,

I would like to be able to print the contents of a canvas. I have tried to create a postscript file, but all I get is a blank canvas. I'm pretty sure that's because this is a container canvas with a bunch of widgets added to it. This is the code I've tried so far:
```
    self.tiCanvas.postscript(file=postscriptFilename, colormode='color')
```
I have attached a screenshot of part of the canvas I am trying to print. It is a visual representation of a student's transcript.

Can anyone offer a suggestion for how to move forward? I have looked around, but haven't found much.

---

### Post by gmargo on 2010-05-31
[http://effbot.org/tkinterbook/canvas.htm#Tkinter.Canvas.postscript-method](http://effbot.org/tkinterbook/canvas.htm#Tkinter.Canvas.postscript-method)

says "Images and embedded widgets are not included.".  Is that the "canvas" that you are talking about?

---

### Post by japhyr on 2010-05-31
Yes, that is the canvas.  But I am open to any suggestions about how to print from a python program.  I haven't found much so far.  I think that's because any search with the word "print" in it is relevant to all kinds of pages related to the print function, and I have also heard that sending things to a printer is much harder than sending things to the screen.  So any leads are appreciated.

---

### Post by Can+~ on 2010-05-31
Edit: ok, I totally misunderstood your problem. But it seems that creating widgets, make them to be "above" the canvas, thus, it won't work at all (as you guessed).

Looking at your table, I would think that it would be easier to just output to html. Or try to recreate it with the tk canvas basic drawing functions instead of widgets.

---

### Post by soltanis on 2010-05-31
You can also try to invoke another program to do a screen capture and print the resulting file. It's a workaround, but I think it's merited here and preferable to re-implementing all the work that has already been done.

---

### Post by japhyr on 2010-06-01
I thought about the screen capture piece, but that seems a pretty ugly workaround.  I think I will play with the other option, even if it's some rewriting.  Do any of you know any good resources for optimizing output for printing?

---

