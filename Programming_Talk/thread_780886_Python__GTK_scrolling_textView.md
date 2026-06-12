---
title: "Python / GTK scrolling textView?"
date: 2008-05-03
forum: Programming Talk
---

### Post by ecs_pf5 on 2008-05-03
I'm trying to pop open a limited-size window, and display some text in it in a vertically scrollable textView:

```




def viewlicense(self, widget, data=None):

    self.windowpop = gtk.Window(gtk.WINDOW_TOPLEVEL)
    self.windowpop.set_size_request(400, 200)
    self.windowpop.set_default_size(400, 200)
    self.windowpop.set_title("Help & Licensing Info")
    
    self.licensescroller = gtk.ScrolledWindow()
    #self.licensescroller.set_size_request(380, 160)
    #self.licensescroller.set_default_size(380, 160)
    self.licensetextarea = gtk.TextView()
    #self.licensetextarea.set_size_request(380, 160)
    #self.licensetextarea.set_default_size(380, 160)

    self.licensescroller.set_child_packing(self.licensetextarea, True, True, 5, gtk.PACK_START)
    self.licensescroller.add(self.licensetextarea)
    
    
    self.licensetextarea.get_buffer().insert_at_cursor('  \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  Edit as necc.\n')
    self.licensetextarea.get_buffer().insert_at_cursor('  \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  Here is a few lines of text for example purpose     \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  Here is a few lines of text for example purpose     \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  Here is a few lines of text for example purpose     \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  Here is a few lines of text for example purpose     \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  Here is a few lines of text for example purpose     \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  Here is a few lines of text for example purpose     \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  Here is a few lines of text for example purpose     \n')
    self.licensetextarea.get_buffer().insert_at_cursor('  \n')

    
    self.licensetextarea.set_editable(False)
    self.licensetextarea.set_cursor_visible(False)
    
    self.licclose = gtk.Button("OK", None, True)
    self.licclose.connect("clicked", self.closelicense, None)
    
    self.licclosecontainerh = gtk.HBox(False, 0)
    self.licclosecontainerh.pack_start(self.licclose, False, False, 5)
    
    self.licensecontainerh = gtk.HBox(False, 0)
    self.licensecontainerv = gtk.VBox(False, 0)
    
    self.licensecontainerh.pack_start(self.licensescroller, False, False, 5)
    
    self.licensecontainerv.pack_start(self.licensecontainerh, False, False, 5)
    self.licensecontainerv.pack_end(self.licclosecontainerh, False, False, 5)
    
    self.windowpop.add(self.licensecontainerv)
    
    self.licclosecontainerh.grab_focus()
    
    self.windowpop.show_all()








```

everything works except I can't set the size of self.licensetextarea - it always either comes up tiny, or else the python won't fire up at all. how can it be done?

[edit]
just tried 

```

self.licensescroller.child_set_property(self.licensetextarea, "height-request", 150)
self.licensescroller.child_set_property(self.licensetextarea, "width-request", 300)

```

to no avail

---

### Post by days_of_ruin on 2008-05-03
[http://www.pygtk.org/pygtk2tutorial/sec-TextViews.html]("http://www.pygtk.org/pygtk2tutorial/sec-TextViews.html")
Hope this helps.

---

### Post by ecs_pf5 on 2008-05-03
yes! :) that helped figure it

and line 56 of the code he posts there helped me getting rid of an unwanted horizontal scrollbar too. Thanks.

I now have working code;

```

def viewhelp(self, widget, data=None):
        
    self.windowpop = gtk.Window(gtk.WINDOW_TOPLEVEL)
    self.windowpop.set_default_size(400, 200)
    self.windowpop.set_title("Help & Licensing Info")
    self.licensescroller = gtk.ScrolledWindow()
    self.licensescroller.set_policy(gtk.POLICY_NEVER, gtk.POLICY_ALWAYS)
    self.licensetextarea = gtk.TextView()
    self.licensescroller.add(self.licensetextarea)



    self.licensetextarea.get_buffer().insert_at_cursor(' License, info & help \n')
    self.licensetextarea.get_buffer().insert_at_cursor(' """""""""""""""""""" \n')
                .
                . yada
                .
    self.licensetextarea.get_buffer().insert_at_cursor('\n')
    self.licensetextarea.get_buffer().insert_at_cursor('\n')



    self.licensetextarea.set_editable(False)
    self.licensetextarea.set_cursor_visible(False)
    self.licensecontainerh = gtk.HBox(False, 5)
    self.licensecontainerh.pack_start(self.licensescroller, True, True, 5)
    self.licclose = gtk.Button("OK", None, True)
    self.licclose.connect("clicked", self.closelicense, None)
    self.licclosecontainerh = gtk.HBox(False, 5)
    self.licclosecontainerh.pack_start(self.licclose, False, False, 5)
    self.licensecontainerv = gtk.VBox(False, 5)
    self.licensecontainerv.pack_start(self.licensecontainerh, True, True, 5)
    self.licensecontainerv.pack_end(self.licclosecontainerh, False, False, 5)
    self.windowpop.add(self.licensecontainerv)
    self.licclose.grab_focus()
    self.windowpop.show_all()

```



[edit]
had a look on 'Thread Tools' to see if I could mark this [solved], but nothing there?

---

