---
title: "Gtk actions, accellerators, glade..."
date: 2010-06-29
forum: Programming Talk
---

### Post by J V on 2010-06-29
I want to pop a menu from a toolbutton... I heard (Or at least, that's what the majority of google heard) that this is most easily done with Actions and Accelerators...

These exist in glade, but I have no idea how I would use them...

I have the menu in glade, I have the button in glade... Anyone know how to get them to work together?

Edit: Also, how would I make the program open my docbook help file? Independent of DE... Or do I just try to run yelp then try to run khelpcenter if it doesn't work?

---

### Post by diesch on 2010-06-29
Use a MenuToolButton and set its menu property to your menu

---

### Post by J V on 2010-06-29
But then you get, in effect, two separate buttons, one behaves like a normal button, the other like a menu button...

---

### Post by J V on 2010-06-30
bump

---

### Post by diesch on 2010-07-01
Seems I don't really understand what you want to do.

---

### Post by J V on 2010-07-01
Normal button, when pressed, popup menu pops up... This should be doable with "Actions" and "Accellerators" seen in glade... Only I can't find any guides on them...

Edit: Ok, a bit more work leads me to believe I need to ignore actions and somehow use gtk.menu.attach_to_widget() to make the menu pop up... That's the right one right? Or do I manually have to program a menu.popup() and popdown() to the buttons signals?

---

### Post by Unterseeboot_234 on 2010-07-02
For me, I found perl / perl-gtk the easiest answer. Glade just writes an <xml> file. The perl-gtk2 lib will magically let you bind buttons to functions, which is cool, you can bolt on another front-end to your logic code.

If you don't want to use perl, then you need the GTKBuilder option of Glade. But, once again, perl can and does use those bindings if desired. GTKBuilder takes some study to discover how to make an Object of the handler that will handshake with your logic code.

[http://ubuntuforums.org/showthread.php?p=9536801#post9536801]("http://ubuntuforums.org/showthread.php?p=9536801#post9536801")

---

### Post by J V on 2010-07-02
That didn't help: I'm asking a very specific question...

Why won't this work:
```
def help_menutoolbutton_clicked(self,widget,event):
        self.helpmenu.popup(None,None,None, event.button, event.time)
        return True
```

---

### Post by Unterseeboot_234 on 2010-07-02
Well, you did't say what language...

def foo( self ) :
// self.result = self.sumthang.wid_woopthang.on_disthang


is python. You will have to wade through the PyGtk tuts.

**[http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm]("http://www.pygtk.org/articles/application-pygtk-glade/Building_an_Application_with_PyGTK_and_Glade.htm")**

**[http://www.pygtk.org/tutorial.html]("http://www.pygtk.org/tutorial.html")**

Or, if you are trying to do this with a shell script??? bash ch is something I keep promising myself I'll get back to. All I can do is VB, java, COBOL, ANSI C, BASIC, php, javascript, cgi (tried pythong and dropped it), but in any event if it isn't java or COBOL I have to refresh myself. And now I've discovered perl and I like it.

With GtkBuilder, the metaphor is you are requesting a node from the <xml> tree into a pyVariable as a type GtkBuilder... IF if you are using python... whereas with the old glib the viewpoint is Document Object Model.

Tell us what language. Binding whatever you named your widget in Glade to a function is trivial.

---

### Post by J V on 2010-07-02
Gtk is a library, it's essentially the same through all languages...

menu.popup in python is gtk_menu_popup() in C, and so on... language is irrelevant here...

---

### Post by J V on 2010-07-04
Ok, it looks like it's just not being called... Somehow the button_press_event isn't connecting with the function...

```
def help_menutoolbutton_clicked(self,widget,event):
        print "Activated"
        self.helpmenu.popup(None,None,None, event.button, event.time)
        pass
``````
GtkWindow.GtkVBox.GtkToolbar.GtkToolbutton.button_press_event = help_menutoolbutton_clicked
```

---

