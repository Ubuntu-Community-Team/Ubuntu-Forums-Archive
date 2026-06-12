---
title: "[GTK]how to manage multiple Gtk windows?"
date: 2009-04-02
forum: Programming Talk
---

### Post by sujoy on 2009-04-02
I have the main window and the about dialog in one glade file and a preferences window in another glade file.

The problem is that I can show the preferences window, but havent yet managed to destroy it. I tried using both the delete event and the destroy signal, still, nothing works(read no activity whatsoever). However, once I close the main window, I can then close the preferences window normally. :confused:

Can someone please guide me to a solution or even a link maybe?

main.c file [here]("http://dpaste.com/22632/")
callback.c file [here]("http://dpaste.com/22633/")
preferences.c file [here]("http://dpaste.com/22634/")

gui.xml file [here]("http://dpaste.com/22636/")
preferences.xml file [here]("http://dpaste.com/22637/")

Another strange thing is that, after preferences window is displayed, if i click the close button on the main_window i quit the main window instantly and then i can click on the close button in preferences to close it normally. However, if after displaying preferences, I click on the quit menu, then nothing happens, and i can either click quit again or close the main_window both of which directly quits the application.

---

### Post by kknd on 2009-04-02
gtk_widget_destroy() destroyes widgets (whoa). But I usually don't destroy widgets that will be used again, I just hide then ( gtk_widget_hide ).

---

### Post by nvteighen on 2009-04-02
> **kknd said:**
> gtk_widget_destroy() destroyes widgets (whoa). But I usually don't destroy widgets that will be used again, I just hide then ( gtk_widget_hide ).
Well, because destroying widgets means to deallocate them.

---

### Post by kknd on 2009-04-02
> **nvteighen said:**
> Well, because destroying widgets means to deallocate them.

Yes. Instead of creating, using, destroying, creating, using, destroying I prefer create, use, hide, show, use, hide, etc.

---

### Post by sujoy on 2009-04-03
Yes I tried gtk_widget_destroy and hide both. Found something interesting that I hadn't noticed before, the preferences window is just displayed, but it is not responsive, that is the button in there is not clickable at all.

---

### Post by kknd on 2009-04-04
Showing a container doesn't shows it's content. You need to do a gtk_widget_show_all to recursively show the contents.

---

### Post by slavik on 2009-04-04
why not combine averything into a single file?

---

### Post by sujoy on 2009-04-05
> **slavik said:**
> why not combine averything into a single file?

Yes I could definitely do that. But this is more of a learning expedition for me than actually making a production system, hence I am just playing around with the options I have.

---

