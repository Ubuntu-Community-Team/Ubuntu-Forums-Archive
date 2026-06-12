---
title: "PYGTK File Chooser Button"
date: 2009-03-25
forum: Programming Talk
---

### Post by Joanofarc on 2009-03-25
Hi, I'm new to programming. And I'm wondering in python using glade3 and pygtk, how do I get the results of the file that the user picked using the File Chooser Button widget into a string.

---

### Post by simeon87 on 2009-03-25
```

dialog.get_filename()

```

There's also documentation about this: [http://www.pygtk.org/docs/pygtk/class-gtkfilechooser.html](http://www.pygtk.org/docs/pygtk/class-gtkfilechooser.html)

---

### Post by Joanofarc on 2009-03-25
No, yes I understand that. I just don't understand how to set it up. I need some hand holding.

---

### Post by simeon87 on 2009-03-25
> **Joanofarc said:**
> No, yes I understand that. I just don't understand how to set it up. I need some hand holding.

Here's an example: [http://www.pygtk.org/pygtk2tutorial/sec-FileChoosers.html](http://www.pygtk.org/pygtk2tutorial/sec-FileChoosers.html) (see bottom of the page).

Not all the code is needed, some code is just used for creating a filter for certain file types.

Edit: or do you mean opening the file and reading the contents?

---

### Post by Joanofarc on 2009-03-25
Ive read over it, I just don't understand how to hook any of that into glade3.

---

### Post by simeon87 on 2009-03-26
> **Joanofarc said:**
> Ive read over it, I just don't understand how to hook any of that into glade3.

Glade is just for designing the windows of your application; you'll have to write code to let the application actually do something. In this case, opening a file is a standard job and there's already a FileChooserDialog for it (which you don't need to design or handle in Glade).

---

