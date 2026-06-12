---
title: "HOWTO: Print on Banner Paper, Continuous Rolls, Custom Paper sizes with xpp"
date: 2007-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by ArtInvent on 2007-12-04
In a nutshell you install a program called xpp, use it's GUI to set a custom paper size, and then print using the 'xpp' command in a print dialog box, instead of the normal 'lp' command.

This has been tested on Feisty using Inkscape 0.45.1 as the graphics program to print from. It just so happens that the graphics I want to print I do in Inkscape. I have not had as much luck with this method in other programs such as Gimp. However, further experiments with this method might get it to work in different programs. If not, it should be possible to convert just about any graphics into a PNG or SVG file, import into Inkscape, and print using this method.

I have an Epson Stylus Photo 1270 wide carriage printer, and have wanted to print on very long continuous sheets of banner paper, but have not been able to until now. The standard CUPS dialog does not have the sizes of paper I wanted; there is a 'Custom' paper size in the drop down box but I have never been able to figure out how to set it to an actual custom size as one would expect. I even installed the KDEPrint packages as I heard these are very good, but I still could not specify custom page sizes.

I was finally able to figure out a method using the package **xpp**. Meaning 'The X Printing Panel', project website at   [http://cups.sourceforge.net/xpp/](http://cups.sourceforge.net/xpp/) 

This is a standard Linux package but you will have to install it with apt or Synaptics. xpp is a kind of an alternate print dialog, you can even print directly from it's GUI with certain types of photo and document files. I don't know all the ins and outs of it, but I did read that it allows one to set up a custom paper size so I thought I would look at it. Once installed, I didn't find a menu item so I started the program in a terminal with the command

[INDENT][FONT="Courier New"]$ xpp[/FONT][/INDENT]

In the GUI, I was able to select the Epson printer, go to 'Options' and set a custom paper size AND actually put in the dimensions of the paper. Every conceivable print option is shown but this is actually the only thing I changed. In my case, I have a sizable quantity of fanfold paper. I have cut it down to 13" wide (the maximum width that the Epson will accept) and I can tear off sheets in increments of 11" in length. In this instance I wanted to print on five segments, one sheet 13" x 55" so this is what I put in the dialogs. 

In Inkscape, I set the document paper size to the same 13" x 55" and positioned my graphics onto the page. 

The Inkscape 0.45.1 print function is primitive at this point, which I have often lamented, but that actually might be better for this purpose. In Inkscape I normally print 'using PostScript operators' and in the Print Destination box, use the 'lp' printer command followed by an option and printer name as follows:

[INDENT][FONT="Courier New"]lp -P Epson-1270[/FONT][/INDENT]

To print using the xpp utility instead, simply change the 'lp' to 'xpp'. My printer command was as follows:
[INDENT]
[FONT="Courier New"]lp -P Epson-1270[/FONT][/INDENT]

Miraculously, the resulting printout was perfect, sized and positioned on the huge banner paper just as in the Inkscape document. (The xpp dialog was even left on 'portrait' mode, while the Inkscape document was laid out as landscape, and the print automatically rotated to the intended orientation.) Sweet.

The one problem I've been having is that many programs don't seem to have an option of using a plain printer command. Lucky for me in most programs I don't need to print on huge paper. Gimp might be one other, and there is a place to put in the 'lp' command, but Gimp has it's own elaborate print set-up dialog and these seem to interfere with the xpp settings. Maybe someone else can help figure this out. Anyone?

---

