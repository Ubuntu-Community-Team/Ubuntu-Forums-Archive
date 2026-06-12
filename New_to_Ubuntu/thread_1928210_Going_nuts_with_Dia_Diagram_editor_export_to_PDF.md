---
title: "Going nuts with Dia Diagram editor export to PDF"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by NerdWermz on 2012-02-19
Hello,

I am starting to learn Dia to do some  of my network drawings but i'm having one problem.
I have the picture drawn and centered on the page, but when i export it to PDF it keeps left hand justifying things.  I have looked through all the settings multiple times all morning without success. 

Could some body please tell me why it does this and how to change it?   I would like the objects to stay centered in the pdf.

thanks.

---

### Post by cotcot on 2012-02-19
Obviously you explored page format and so on.
As a work around you could draw a line around your drawing to show the outer limit and center the drawing within this line. Make the line white if you do not want to see it on the pdf.

---

### Post by NerdWermz on 2012-02-19
Yup, about a hundred times or so.   lol

Only thing under there is:
Paper size
Orientation
Margins
and 
Scaling, I've even tried numerous scaling settings. they all have the same affect.

I think you're onto something. I will draw one big rectangle to represent my printed space and see what that does.

---

### Post by NerdWermz on 2012-02-20
Did some experimenting and the perimeter box was clunky at best.  Everything kept trying to snap to it, and even with the center transparent I still kept grabbing it.

I did find a better work around for now.
Export it as a .eps file then open Scribus and set the page size i want, then import the eps file and save as pdf.  

I think it works pretty well.

---

### Post by cotcot on 2012-03-24
Put the white box on a different layer and put the layer to the background.

---

