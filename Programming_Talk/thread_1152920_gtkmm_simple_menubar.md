---
title: "gtkmm simple menubar"
date: 2009-05-08
forum: Programming Talk
---

### Post by c174 on 2009-05-08
I'm starting to learn gtkmm-2.4. I have read the first chapters of the tutorial up to the one on "Menus and Toolbars". There it suggests to create a menu bar using ActionGroup and UIManager together with an XML-string to layout the menus.

As a newbee I have the following questions:

1) Using MenuBar and related classes directlt seem complicated - need to derive my own class from MenuBar, "difficult" to insert items using Menu_Helpers, need to use *manage( ... ) to build the Menus (the drop down menus) that will be put into the MenuBar. Is there not a simpler way?

2) If I go for the ActionGroup etc method, will I need to generate an XML-string inside the program if I want to change the contents of a Menu during runtime?

Any suggestion for how I can proceed, links to things I should read, or examples a highly appriciated :)

---

### Post by C-- on 2009-05-12
If you want to change menu contents at runtime I cannot help you, although I would imagine regenerating and re-parsing XML strings would be inefficient.

If you want to keep them static I would recommend building the menus in Glade and then parsing the resulting XML at runtime. Glade allows you to graphically build GTK+ GUIs and set properties/handler functions (you still have to define handler implementations in your code). In fact, I would recommend you build your entire GUI in glade.

---

