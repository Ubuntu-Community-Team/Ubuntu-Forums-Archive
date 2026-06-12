---
title: "Gtkmm: Change Cursor Problem"
date: 2012-08-15
forum: Programming Talk
---

### Post by fallenshadow on 2012-08-15
So I have done some code to change cursor. This code causes a segmentation fault. I know that this is because.. 

```
Glib::RefPtr <Gdk::Window> ref_Gdk_window = get_window(); 
``` 

..returns null. In order to get a proper value returned the window needs to be realized apparently.

I have tried this already: 

> window->realize();

It failed... :(

How can I get this "realized" thing to work?

---

### Post by PaulM1985 on 2012-08-15
Maybe this will help:

[http://old.nabble.com/How-to-use-get_window()-function--td18815687.html](http://old.nabble.com/How-to-use-get_window()-function--td18815687.html)

It sounds like you first need to have a window before you can get it.

Paul

---

### Post by fallenshadow on 2012-08-15
..but I do have a window. :/

Maybe it needs to be a gdk window and not a gtk window?? o_O

---

### Post by fallenshadow on 2012-08-20
...bump?! :p

---

### Post by Hetepeperfan on 2012-08-20
> **fallenshadow said:**
> So I have done some code to change cursor. This code causes a segmentation fault. I know that this is because.. 

```
Glib::RefPtr <Gdk::Window> ref_Gdk_window = get_window(); 
```..returns null. In order to get a proper value returned the window needs to be realized apparently.

I have tried this already: 



It failed... :(

How can I get this "realized" thing to work?

have you allready run YourWindow.show()? I thought in gtk you must have allready shown the window and then it get realized as well.

---

### Post by fallenshadow on 2012-08-21
Holy crap! :D

> ref_Gdk_window value: 1

Thanks! 

EDIT:

Ok the cursor changes but it creates a new small GTK window and only the cursor is changed for that window.

---

### Post by fallenshadow on 2012-09-04
Right so now I have the cursor changing on the mainwindow. (thanks to a little help) ;)

Only thing is that my custom cursors no longer work! :o

Is there any alternative ways to set it other than this?:

```
Glib::RefPtr<Gdk::Cursor> display_cursor = Gdk::Cursor::create(ref_Gdk_window->get_display(),Gdk::Pixbuf::create_from_file (pathname),0,0);
  ref_Gdk_window->set_cursor(display_cursor);
```

Help on this is greatly appreciated! :)

---

