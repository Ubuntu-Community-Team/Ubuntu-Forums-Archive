---
title: "How to add icon to button in Pygtk?"
date: 2006-06-30
forum: Programming Talk
---

### Post by chanders on 2006-06-30
Hi all.. I am trying to add a system icon to a button in a pygtk app I am writing. I am having two problems and I was wondering if anyone can help me out...

1. How do I access the gnome icons in the current theme? Eg. If I want to access the 'printers' icon in the current theme I am using, how do I go that?

2. When I add a icon/picture to a button it erases the text that is on the button! How do I change the current icon on the button to another without overwriting the label etc?

Thanks!

---

### Post by Daverz on 2006-06-30
I think you need to use gnome-python if you want to access stock gnome (not just gtk) icons, though I could be wrong.  You can always include the icon files with your source and use the method here:

[http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq08.012.htp](http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq08.012.htp)

If you want to have an icon and a label in your button, you'll need to add those to some container like an hbox and add that to the button

hbox = gtk.HBox()
hbox.pack_start(mylabel)
hbox.pack_start(myimage)
button.add(hbox)

---

### Post by chanders on 2006-06-30
[QUOTE=Daverz]I think you need to use gnome-python if you want to access stock gnome (not just gtk) icons, though I could be wrong.  You can always include the icon files with your source and use the method here:

[http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq08.012.htp](http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq08.012.htp)

If you want to have an icon and a label in your button, you'll need to add those to some container like an hbox and add that to the button

hbox = gtk.HBox()
hbox.pack_start(mylabel)
hbox.pack_start(myimage)
button.add(hbox)[/QUOTE]

Thanks for your reply, I am using a Glade file to load the UI. The glade file has all of the info such as the button label etc. It has a generic icon that is supposed to be changed at runtime.

If I were to use your method as above it would nullify using a Glade file in the first place. There must be some way to just change the stock image that was added in the glade file on the fly without overwriting the labels :-k 

I could package the icons with the app, but why do that when they are available on the users computer?! :mad:

---

### Post by Daverz on 2006-06-30
You can dig into the children of the button to get the Image and change the pixbuf it's using.

True, the icons are probably on the users computer if they are already using Gnome, but to access them by stock-id adds a gnome dependency to your program.  If you don't mind that, then make your project a gnome project.    

I don't bother with glade these days as it only does the easy stuff (box layout) and punts on the hard stuff (uimanager, treeview columns, etc), and there are some things you can only do if you subclass widgets (like adding keybindings to a widget).  Also, I have a lot of repetitive layout which is easier to do with a for loop than a lot of cutting and pasting in glade.

---

### Post by chanders on 2006-06-30
I have to agree with you about glade. It's really only for the easy stuff. I will take your adice and convert the project into a gnome project as it is gnome specific. 

Any help you have on this would also help, I'm off to google, even though I suspect it's something like adding an 'import gnome-something' at the start of the .py file....

Thanks again..

---

### Post by Daverz on 2006-06-30
I seem to have missed this gtk function:

gtk.image_new_from_icon_name(icon_name, icon_size)

[http://pygtk.org/pygtk2reference/class-gtkimage.html](http://pygtk.org/pygtk2reference/class-gtkimage.html)

Try this with the string for the theme icon.  However, the user might not have the icon in their theme, in which case you should fall back to loading it from a file.

---

### Post by Daverz on 2006-06-30
[QUOTE=Daverz]I seem to have missed this gtk function:

gtk.image_new_from_icon_name(icon_name, icon_size)

[http://pygtk.org/pygtk2reference/class-gtkimage.html](http://pygtk.org/pygtk2reference/class-gtkimage.html)

Try this with the string for the theme icon.  However, the user might not have the icon in their theme, in which case you should fall back to loading it from a file.[/QUOTE]

Well, this doesn't work for gnome stock icons.  It does work for theme icons that aren't stock icons like 'gtk-goto-last-ltr' in the Human theme.

---

### Post by Daverz on 2006-06-30
Sorry for talking to myself, but 'gtk-goto-last-ltr' is just the left-to-right version of gtk.STOCK_GOTO_LAST.  

Still, you might want to look over this part of the reference manual:

[http://pygtk.org/pygtk2reference/class-gtkicontheme.html](http://pygtk.org/pygtk2reference/class-gtkicontheme.html)

---

### Post by chanders on 2006-07-01
[QUOTE=Daverz]Sorry for talking to myself, but 'gtk-goto-last-ltr' is just the left-to-right version of gtk.STOCK_GOTO_LAST.  

Still, you might want to look over this part of the reference manual:

[http://pygtk.org/pygtk2reference/class-gtkicontheme.html](http://pygtk.org/pygtk2reference/class-gtkicontheme.html)[/QUOTE]

You're not talking to your self :-)... I am trying your suggestions... Will let you know  if I suceed/not....

[QUOTE=Daverz]You can dig into the children of the button to get the Image and change the pixbuf it's using.[/QUOTE]
Can this be done by direct assignment?

---

### Post by Daverz on 2006-07-01
OK, this should be my last reply to myself :p

Using image_new_from_icon_name *will* will allow you to use stock gnome icons if they are in the theme.  I got confused because the names aren't necessarily the same as those you see in glade.  For example, 'gnome-stock-midi' in glade is just 'stock_midi' when you look it up in the default theme.  You can get a list by getting the default theme

theme = gtk.icon_theme_get_default()
print theme.list_icons()

Unless you know your app will only be used in a gnome environment (e.g. an applet), you should use theme.lookup_icon(), and if it's not there load it from a file using the method given in the FAQ.  I'll try to remember to update the FAQ to mention gtk.image_new_from_icon_name().

---

### Post by Daverz on 2006-07-01
On further investigation, actually making the theme icon names usable (e.g. in uimanager's XML definition) is fiddly.  But a fix is coming in 2.10:

[http://bugzilla.gnome.org/show_bug.cgi?id=323484](http://bugzilla.gnome.org/show_bug.cgi?id=323484)

If you just want to get an image to use in a button it's not hard, just follow the IconTheme API.

---

### Post by chanders on 2006-07-01
Thanks! 
I finally got it working with this piece of code...

```
        #Assign icons to Items
        MyTheme = gtk.icon_theme_get_default()
        MyIconPixbuf = MyTheme.load_icon("gnome-dev-mouse-ball", 36, gtk.ICON_LOOKUP_FORCE_SVG)
        self.wTree.get_widget("image1").set_from_pixbuf(MyIconPixbuf)

```

---

### Post by Daverz on 2006-07-02
[QUOTE=chanders]Thanks! 
I finally got it working with this piece of code...

```
        #Assign icons to Items
        MyTheme = gtk.icon_theme_get_default()
        MyIconPixbuf = MyTheme.load_icon("gnome-dev-mouse-ball", 36, gtk.ICON_LOOKUP_FORCE_SVG)
        self.wTree.get_widget("image1").set_from_pixbuf(MyIconPixbuf)

```[/QUOTE]

Or         

  self.wTree.get_widget("image1").set_from_icon_name('gnome-dev-mouse-ball', 36)

which has the advantage that it won't raise an exception if gnome-dev-mouse-ball isn't on the user's system.

---

