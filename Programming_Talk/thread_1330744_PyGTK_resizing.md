---
title: "PyGTK resizing"
date: 2009-11-18
forum: Programming Talk
---

### Post by exutable on 2009-11-18
Hey guys,

I am creating an app to interface with ARM7 Atmel microcontrollers.

I'm having a little trouble with PyGTK resizing.  My virtual terminals want to stay a fixed size but I want them much smaller,  I'm currently using a table with a vbox in it for the terminals.  I have tried enabling scrolling which helped a little but I couldn't really control the size, I tried hpaned but that didn't really work either.

There is a screenshot attached, currently the window is way too big.  I want it resizable, buttons and all.

Here is the pygtk code that is relevant:
```
hbox = gtk.HBox(homogeneous=True, spacing=1)
	hbox.pack_start(self.terminal1, expand=True, fill=True, padding=0)
	hbox.pack_start(self.terminal2, expand=True, fill=True, padding=0)

	#Create the table and insert all the items
	table = gtk.Table(rows=5, columns=2, homogeneous=False)
	table.attach(menuBar, 0, 2, 0, 1)
	table.attach(self.startserver_btn, 0, 1, 1, 2)
	table.attach(self.stopserver_btn, 0, 1, 2, 3)
	table.attach(self.connect_btn, 1, 2, 1, 2)
	table.attach(self.disconnect_btn, 1, 2, 2, 3)
	table.attach(self.writeimage_btn, 1, 2, 3, 4)
	table.attach(hbox, 0, 2, 4, 5)
	#table.attach(self.terminal2, 1, 2, 4, 5)

	#Now add the table and show it all	
	self.add(table)
	self.show_all()
```

---

### Post by meson2439 on 2009-11-19
I don't know if this relevant but I noticed that a lot of gtk apps cannot be resized into something smaller than the content it has. Had you tried placing the table inside another box before placing it into hbox?

---

### Post by exutable on 2009-11-19
Yes,

I think I know what you're saying.  I've tried to force the table to be a certain size but it doesn't really have any effect on it.

---

### Post by SledgeHammer_999 on 2009-11-19
If you want your terminals to be an EXACT size and not resize them, then use a GtkFixed container.

---

### Post by exutable on 2009-11-19
My understanding of fixed containers was that it changed position more than size?

---

### Post by SledgeHammer_999 on 2009-11-19
yes they don't change the size of their child widgets. Instead use on the widgets the "gtk_widget_set_size_request()".

---

### Post by exutable on 2009-11-19
Ok so the fixed containers kind of work but they cut some of the terminal off at the bottom, I basically want the same resize function that gnome-terminal does.

Anybody know about this?

---

### Post by exutable on 2009-11-19
I think the problem is that there isn't any documentation for python-vte, if there was, it would actually be fairly simple to change the size of the terminal.

[http://library.gnome.org/devel/vte/unstable/VteTerminal.html#vte-terminal-set-size]("http://library.gnome.org/devel/vte/unstable/VteTerminal.html#vte-terminal-set-size")

I found this on changing the size of a virtual terminal

---

