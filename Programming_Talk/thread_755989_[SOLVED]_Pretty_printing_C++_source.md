---
title: "[SOLVED] Pretty printing C++ source"
date: 2008-04-15
forum: Programming Talk
---

### Post by public_void on 2008-04-15
I'm looking for a tool, tools or technique to help add a C++ code for a function to an Open Office document. I'd like to have it in colour (or at least bold) highlighted keywords and strings, and if possible as an image. I've tried some tools such as trueprint to convert to postscript, then ps2eps and the imagemagick tool convert to convert to png. However that resulted in a blank image. I know of src2tex and src2latex, but I'm not sure about converting to png, or if converting to tex or latex, or even postscript formats is the right way of going about this. Am I missing something obvious?

Any help is much appreciated.

---

### Post by CptPicard on 2008-04-15
Have you tried **a2ps**?

---

### Post by dwhitney67 on 2008-04-15
Do some research into "a2ps" (ascii-to-postscript).  This venerable tool that has been around for years, on both Linux and Unix systems.  It works like a charm!
```

sudo apt-get install a2ps
```

Here's the site for the documentation:  [http://www.gnu.org/software/a2ps/](http://www.gnu.org/software/a2ps/)

---

### Post by vexorian on 2008-04-15
This is what I do:
- I got gVim with custom syntax highlighting, I got a black and white (using bold) one for printing, once I needed color and just used vexorian.vim :)

- Then I use gVim's option to convert to html.

- This allows me to import the html file in openOffice.

---

### Post by public_void on 2008-04-15
I found what I was looking for in [source-highlight]("http://www.gnu.org/software/src-highlite/"). It does coloured syntax highlighting but can produces HTML output, something that OpenOffice likes.

Thanks for the help anyway.

---

