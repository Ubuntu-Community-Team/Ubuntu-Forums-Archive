---
title: "Python, glade, grab input from a combo box and file chooser."
date: 2009-10-09
forum: Programming Talk
---

### Post by talsemgeest on 2009-10-09
Hey all, I'm still learning python and glade, but unfortunately there doesnt seem to be a lot of tutorials for using python with glade. Creating the interface I can do, but getting python to connect to it is what I'm having trouble with. For example, the lines ```
vidcombo = self.widgets.get_widget("vidcombo")
print vidcombo
``` only gives me ```
<gtk.ComboBox object at 0xff29b0 (GtkComboBox at 0x113e9c0)>
``` I need to get what is selected in the combo box into my python backend, as a string. What is the best way to do this?

---

### Post by eightmillion on 2009-10-10
I've never done anything with glade, but it appears that you have to use a method like "vidcombo.get_active_text()" to get the text or "vidcombo.get_active()" to get the index of the selected Item. Right now you're just printing the string representation of the combobox object. You might want to take a look at the [class reference]("http://www.pygtk.org/docs/pygtk/class-gtkcombobox.html") if you haven't already.

---

### Post by talsemgeest on 2009-10-10
Brilliant, looks like you did it eightmillion! I'm still learning and really appreciate the help, and I'm still on the lookout for places to learn these kinds of things. :)

Thanks again :)

---

### Post by eightmillion on 2009-10-10
No problem. I'm glad I could help. :)

---

