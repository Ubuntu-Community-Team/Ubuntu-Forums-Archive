---
title: "pyGTK: flag for a closed window?"
date: 2008-01-06
forum: Programming Talk
---

### Post by ryeterrell on 2008-01-06
Is there some sort of flag for a window that will let me know when it is closed in pygtk?  Something like window.closed?  I want to set up a loop as such:

```

while window.isOpen():
    while gtk.events_pending():
        gtk.main_iteration()

```

So, what is this isOpen() function or flag?  I've been looking for quite a while and see nothing!

---

### Post by Quikee on 2008-01-06
> **ryeterrell said:**
> Is there some sort of flag for a window that will let me know when it is closed in pygtk?  Something like window.closed?  I want to set up a loop as such:

```

while window.isOpen():
    while gtk.events_pending():
        gtk.main_iteration()

```

So, what is this isOpen() function or flag?  I've been looking for quite a while and see nothing!

You mean window visibility (hidden/shown)? Because if a window is closed it is destroyed as far as I know. ;) 

You can get the visibility with:
[PHP]widget.get_property("visible")[/PHP]

And set it with:
[PHP]widget.set_property("visible", True)[/PHP]
or
[PHP]
widget.show()
widget.hide()[/PHP]

---

### Post by ryeterrell on 2008-01-06
Destroyed is fine.  How do I check to see if my window is destroyed?  Thanks.

---

### Post by Quikee on 2008-01-06
> **ryeterrell said:**
> Destroyed is fine.  How do I check to see if my window is destroyed?  Thanks.

Destroyed means - it does not exist anymore. The only thing you can do is to respond to windows "destroy-event" and flag yourself if window is destroyed. 

Maybe it would be better if you explain in more detail what you want to do.

---

### Post by ryeterrell on 2008-01-06
Well, if I have some window, and I close it, and then I print the variable that was pointing to the window, it is not "None".  It is some window.

If I could make it so that it was "None" after closing the window, that would work great.

---

### Post by Quikee on 2008-01-07
> **ryeterrell said:**
> Well, if I have some window, and I close it, and then I print the variable that was pointing to the window, it is not "None".  It is some window.

If I could make it so that it was "None" after closing the window, that would work great.

You can't make it None by itself, but you can make it like I said above. When destroy event happens you could create a flag on the window.

...
[PHP]window.connect('destroy', onDestroy)[/PHP]
...

[PHP]def onDestroy(widget):
	widget.destroyed = True[/PHP]
...

[PHP]if has_attr(window, 'destroyed') and window.destroyed:
	print "window has been destroyed"[/PHP]

Also look [here]("http://www.pygtk.org/docs/pygtk/class-gtkobject.html"). flags() with gtk.IN_DESTRUCTION might also work.

---

### Post by slavik on 2008-01-07
when a window is about to close it emits a delete event, once the window is closed, it emits the destroy event.

---

