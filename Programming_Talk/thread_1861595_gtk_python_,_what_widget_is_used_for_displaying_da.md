---
title: "gtk python , what widget is used for displaying data i.e a webpage or list of files"
date: 2011-10-15
forum: Programming Talk
---

### Post by mushy365 on 2011-10-15
ive been doing a gtk python tutorial and trying to learn gui, ive got buttons and stuff done, but im not sure what widget is used to display like a file listing where you might have a picture and then a file name and then an option to highlight

i thought it was a comboBox but when i created a combo box it wouldnt let me write any information to it when the button was pressed. i looked up the error and told me to use combo_box_new_text but that again is like a  textbox with a drop down list, i dont want to type directly into the box, its ment to be a display box. 

any help please

---

### Post by satsujinka on 2011-10-15
Displaying a list is kind of a pain...
If you want you can gather the list into strings and put them in a label (probably the easiest solution, though maybe not exactly what you're looking for.)
Otherwise, the best solution is probably either a treeview or an iconview. If you can't find any information on them, I suppose I can walk you through their creation, but I can't say I'm exactly a master on the subject.

---

### Post by mushy365 on 2011-10-16
thanks, ill be fine getting the info just couldnt find a widget to do what i wanted.

In ubuntu software manager, what widget are they using there? Its like a white box then when you search you get an image the program name and you can highlight it.

---

### Post by satsujinka on 2011-10-16
It uses iconview. Well, a couple heavily modified ones to be more accurate, but it does use iconview.

---

