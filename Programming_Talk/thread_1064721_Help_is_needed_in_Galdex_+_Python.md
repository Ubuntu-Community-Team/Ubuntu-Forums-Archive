---
title: "Help is needed in Galdex + Python"
date: 2009-02-09
forum: Programming Talk
---

### Post by Voland on 2009-02-09
Guys, I'm new in Python programming. I've tried GTK+ and C, but Python seems to be easier. I've created glade file, parsed it with Gladex and got two .py files - main and callbacks. Now I need to write callbacks functions, but I can't understand how to get access to widgets. 
For example I have 3 entry boxes, 1 combobox, 3 buttons in my glade file. I have in the callbacks file : > def on_OperationComboBox_changed(widget, data, wtree):
	print "function 'on_OperationComboBox_changed' not implemented"
	pass
In this function I want to get 1 selected by user of 4 predefined in glade file elements. How can I do this?

---

### Post by Voland on 2009-02-10
Well, it seems I can get access to one widget using "widget" argument, but what if I need to get access to another one in this function? I guess "wtree" could help, but how?

---

### Post by kknd on 2009-02-10
Usually you would need to get a reference to the widget ( something like gladeobj.getWidget(widgetName) ). I don't know Gladex, but its probable that Gladex has done this for you in the main file.

---

### Post by Voland on 2009-02-10
Thanks for your reply.
Here they are my files. Could you help me to figure out where I can find it?

---

