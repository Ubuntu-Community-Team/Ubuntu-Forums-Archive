---
title: "Wordwrap labels in GTK"
date: 2007-10-02
forum: Programming Talk
---

### Post by mssever on 2007-10-02
How do you wordwrap labels in GTK? I've got a Glade file (attached) that includes some long labels which make the whole window look wrong. Clearly, manually inserting line breaks is the wrong solution, since manual line breaks look bad if the window is resized or the user specifies a font different from what I'm using.

---

### Post by mssever on 2007-10-03
bump

---

### Post by mssever on 2007-10-03
Bump.

Is this question hard, or is it unclear? I come from a web background, and GUI design seems to be excessively difficult...

---

### Post by PaulFr on 2007-10-04
I do not have much experience with Glade, but was interested to try out your problem, so here is what I found:

I assume you are expecting a row with a label that automatically wraps to become multi-line based on the actual width of the window.

With a bit of poking around in Glade, I set up a Horizontal Box (2 columns, homogeneous) in one row of a Vertical Box (n rows). Then in the first column of the Horizontal Box (where you have the long label), I inserted a Text View. This inserted a scrolled window and inside that a text view. In the second column of the horizontal box, I inserted a Text Entry widget. Since the horizontal box was defined as homogeneous, each column occupies 50% of the width of the dialog.

On the widget tree, I selected the scrolled window, and set the H and V Policy to Automatic to only show scroll bars if needed. Now entering long text in the text view and disabling all sensitivity, editable and focus for the text view seems to give you a multi-line label that reformats the text automatically as the window is resized.

Does this help ?

---

### Post by mssever on 2007-10-05
Thanks for the suggestion. I'll try it as soon as I get a chance. Right now I'm too busy with other things...

---

