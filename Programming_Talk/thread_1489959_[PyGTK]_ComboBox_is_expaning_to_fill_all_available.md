---
title: "[PyGTK] ComboBox is expaning to fill all available space."
date: 2010-05-21
forum: Programming Talk
---

### Post by durand on 2010-05-21
Hi,

I've got this really annoying problem where my combobox is just filling up the space it gets rather than sticking to it's size like the textbox next to it. I've attached a screenshot of the problem.

The code is pastebinned here: [http://pastebin.com/3DXCetvn](http://pastebin.com/3DXCetvn)
though it's pretty simple really. I've got a table with 4 columns and 2 rows and a textbox fills 3 columns in one row and the combobox fills the other column in the one row. The second row contains other stuff. I'm not really sure why this isn't working. If the second row contents expand fully, then the combobox sorts itself out, otherwise it doesn't :(

Can someone help please? Thanks!

---

### Post by StephenF on 2010-05-21
Tables can be tricky to work with.

You could try a VBox containing a HBox for the top line.

---

### Post by durand on 2010-05-21
Okay, I'm trying that now. I get really confused with HBox and VBoxes :S

---

### Post by durand on 2010-05-21
Ah. I did what you said (Entry and Combo inside Hbox inside Vbox) and it now looks exactly the same :(.

---

### Post by durand on 2010-05-21
Woo! Solved it by adding a yoptions=gtk.SHRINK to the table attach function.

---

### Post by Tony Flury on 2010-05-22
I would strongly recommend that you learn GTK packing systems of HBox, VBox with the relevant Pack before and after, and expand and fill options.
They dp provide a far more flexible structure for drawing GUIs than for instance do tables. They do take some getting used to though.

---

### Post by durand on 2010-05-22
Ok. I will probably use them more often, I just thought that tables were more straightforward for this kind of layout.

---

### Post by StephenF on 2010-05-22
Tables are more for aligning widgets into a flexible grid and generally a large one, think spreadsheet.

VBox and HBox should be the mainstay of widget alignment with careful selection of the expand and fill options of Box.pack_start and the set_spacing and set_border_width methods. I advise setting expand=False on your packing of widgets to be changed later as needed for sensible alignment at a variety of window sizes.

Refer to the PyGTK tutorial.

---

### Post by durand on 2010-05-22
Okay. I'll convert my app into a table free one :).

---

### Post by durand on 2010-05-23
Converted the layout to boxes. It looks much nicer now. Thanks :)

---

