---
title: "print without opening file"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Unstuck on 2008-08-09
Often, I want to print a document without opening the file.  It takes too long and seems unnecessary.  Is it possible add an option that allows you to right-click the document's icon and select a print option?  That would be, like, totally awesome. :guitar:

---

### Post by aloshbennett on 2008-08-10
cupsdoprint :)

you could write a wrapper script which invokes the cupsdoprint with the printer and file details. the wrapper script can be added as a nautilus script. That would bring it up when you right click the document.

---

### Post by Unstuck on 2008-08-10
cool, thanks...this is something i've wanted to get into...how do i get started?

---

### Post by aloshbennett on 2008-08-11
To start with, you could have a script file containing

> 
#!/bin/bash
cupsdoprint -P PDF $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS


To add it as a nautilus script, create a soft link under ~/.gnome2/nautilus-scripts and give a nice name, like 'Print File'.

I just have the pdf printer. There must be a way to find the default printer as well.
cupsdoprint takes care of ascii and basic file types.

Right-click and printing is a cool idea! It would be awesome if it would work for major file types.

---

