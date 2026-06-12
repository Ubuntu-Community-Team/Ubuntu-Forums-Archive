---
title: "latex or mathml to image"
date: 2011-03-02
forum: Programming Talk
---

### Post by sidious1741 on 2011-03-02
I thought this was a simple desire. All I want is someway to take some mathematical expression in latex, mathml, or whatever else, and get an image with python. I have tried so many different things and read so many different forums. I see plenty of ways of reading the format but no ways of sending it strait to a picture. This has been beyond frustrating. Thanks so much for the help.

---

### Post by foxmuldr on 2011-03-03
> **sidious1741 said:**
> I thought this was a simple desire. All I want is someway to take some mathematical expression in latex, mathml, or whatever else, and get an image with python. I have tried so many different things and read so many different forums. I see plenty of ways of reading the format but no ways of sending it strait to a picture. This has been beyond frustrating. Thanks so much for the help.

There's a GNU project called Matlab that is meant to work like Maple or Mathematica. It likely has the library functions you need. If you build around that, it should work.

If you're looking for the expression itself as a visualization in text, then look to OpenOffice or LibreOffice and their equation editor. You could use Mago to launch the app, input the expression and capture the image.

If you already have an app which does the expression, search for screen capture apos which will capture the bitmap, then use the GIMP libraries to manipulate the data.

- Rick C. Hodgin

---

### Post by Some Penguin on 2011-03-03
.tex -> .dvi via LaTeX, .dvi -> .ps or whatever (e.g. dvips)

---

### Post by sidious1741 on 2011-03-06
Thanks but I must not have been very clear in my original post. I put this under programming talk because i want to do it with python. I know about open office and other ways to show the image. what i really want is a way to take any input and generate the image. i mean i want something kind of like open office, but something i made. i dont want to go into detail about my project because it is beyond the scope of this thread but say i wanted to make a very simple open office formula editor where given an input, i update an image of the formula.

---

