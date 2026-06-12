---
title: "Focusing on gtk.Entry in gnomeapplet [python]"
date: 2009-07-13
forum: Programming Talk
---

### Post by Shootfast on 2009-07-13
Hi folks,

I'm trying to make a simple bonobo gnomeapplet in python and I've hit a bit of a snag.
I can create the applet OK, and even have the gtk.Entry text box appear, but I am unable to click on the box to start typing. Only when there is another applet with a text box along side (such as desktop search) can I get focus on the text box. I can copy and paste into the box, just not type.

Here is some of the relevant code:

```

def applet_factory(gnome_applet, iid): 

   entry = gtk.Entry()
   entry.set_text("Enter numbers here")
   gnome_applet.add(entry)
   gnome_applet.show_all()        
   return True

```

I've tried differing types of do_grab_focus to no avail. Any help would be awesome. 

Thanks!

---

### Post by ideamonk on 2009-10-10
Hi,

I was into the same issue unless I ran into this paste by some random google search and observed that one needs to call applet.request_focus() to get the Entry activated. In my case I've 
done this on the button_press_event

```
def on_txtFoo_button_press_event(self, widget,event):
		''' give the focus to Applet so that Entry is accessible '''
		self.applet.request_focus(long(event.time))
```

Thanks for putting this up.
:guitar:

---

