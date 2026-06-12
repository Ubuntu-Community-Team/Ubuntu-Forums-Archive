---
title: "How do I add events to a gtk.Image?"
date: 2008-02-25
forum: Programming Talk
---

### Post by solarwind on 2008-02-25
```

def factory(applet, iid):
	image = gtk.Image()
	image.set_from_file("/usr/share/icons/gnome/22x22/emblems/emblem-system.png")

	ebox = gtk.EventBox()
	ebox.connect("button_press_event", showMenu, applet)

	applet.add(image)
	applet.add(ebox)	
	
	applet.show_all()
	return True
```

I'm trying to make a Gnome panel applet that shows an image but acts like a button (just like most panel applets). However, as stated [here]("http://www.pygtk.org/docs/pygtk/class-gtkimage.html"), gtk.Image can not respond to events and must take events from a [gtk.EventBox]("http://www.pygtk.org/docs/pygtk/class-gtkeventbox.html") but I don't know how to do this. Can someone please help?

---

### Post by kknd on 2008-03-15
In fact, it is button-press-event.

Lua example:

[PHP]
require("lgui")

local window = lgui.Window.new()
local box = lgui.EventBox.new()
local label = lgui.Label.new("test")

box:add(label)
window:add(box)

box:connect("button-press-event", lgui.quit)

window:showAll()

lgui.main()
[/PHP]

---

### Post by solarwind on 2008-03-15
> **kknd said:**
> In fact, it is button-press-event.

Lua example:

[PHP]
require("lgui")

local window = lgui.Window.new()
local box = lgui.EventBox.new()
local label = lgui.Label.new("test")

box:add(label)
window:add(box)

box:connect("button-press-event", lgui.quit)

window:showAll()

lgui.main()
[/PHP]

Thanks. I already figured it out though :D

---

