---
title: "string display widget"
date: 2008-02-22
forum: Programming Talk
---

### Post by machoo02 on 2008-02-22
I have a quick question about GUI programming.  I am interested in designing a DNA sequence editor in Python, but I am having trouble figuring out what sort of widget to use to actually display the sequences.  I'm modeling this program after another DNA sequence editor that is only available for Windows: [BioEdit]("http://www.mbio.ncsu.edu/BioEdit/bioedit.html").  An example screenshot is attached.

The string display widget would need some basic formatting capabilities (e.g., text and background color on a per character basis).  I haven't decided on a GUI toolkit as of yet, but I'm interested in using something that is cross-platform (as I'd like to make this editor available for Linux/Win/OS X).  Any suggestions would be appreciated.

Cheers,
-machoo02

---

### Post by LaRoza on 2008-02-22
I don't have much experience in GUI's, but wxWidgets might be worth looking into. [http://www.wxwidgets.org/](http://www.wxwidgets.org/)

---

### Post by machoo02 on 2008-02-22
I've looked into wxWidgets a bit, but in my searches I haven't figured out which of the wxText or wxString widgets could display sequences how I would like.  I could probably try to create my own widget to do this, but I'd like to use as many built in widgets as possible (to reduce the complexity and development time - I'll be learning the GUI toolkit as I go along).

I've also started to look at PyQt as well, which looks like it has slightly more fine grained control over how text can be displayed.

---

### Post by machoo02 on 2008-02-25
Bump.  Can anyone recommend any good forums for either wxPython or PyQt where I could pose this question as well?

---

### Post by lnostdal on 2008-02-25
> **machoo02 said:**
> Bump.  Can anyone recommend any good forums for either wxPython or PyQt where I could pose this question as well?

try their mailinglists

---

### Post by a9bejo on 2008-02-25
The main frame looks like a table widget, with each column containing a character. The one on the left looks like a simple list.

I am sure most GUI Frameworks for Python (Tk,Swing,GTK,QT,...) come with a good table widget where you can modify the background color of single cells and do event handling. I know javax.swing.JTable can do this. 

In any case, I recommend you take a look at the [BioPython](http://biopython.org/wiki/Main_Page) project, if you do not know that already.

---

### Post by machoo02 on 2008-02-25
Thanks for the suggestion, a9bejo.  I'll look into the table widget idea.  Yes, I do know about Biopython, and plan on using it extensively to do a lot of the sequence manipulation and file formatiing.  Too bad they don't have any GUI tools....

---

