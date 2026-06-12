---
title: "How-To: Search in files with GEdit"
date: 2007-08-28
forum: Outdated Tutorials &amp; Tips
---

### Post by ralf57 on 2007-08-28
One of the missing features of Gedit is the "search in files" functionality.
I'm going to describe how this can be easily added without installing any additional plugin.
This method uses the "External tools" plugin (which comes in bundle with gedit) and "Gnome Search Tool" (gnome's default search tool).
Let's go!

1) open Gedit and enable the "External tools" plugin in Edit >> Preferences >> Plugin
2) don't close the dialog but select the plugin and click "Configure plugin" instead
3) let's add a new tool with the following properties
	
	Name : Find in files (or whatever you want)
	Description : Find in files (or whatever you want)
	Accelerator (the keybord shortcut) : type  <Control><Shift>f  (or whatever you want - be sure it's not already used)
	Command :
	
	```

	#!/bin/sh
	xargs gnome-search-tool --contains
	
```
	
	Input : current selection
	Output: bottom panel
	Scope: all documents
	
4) Close the dialog

That's all.
You can test the newly added tool via the shortcut you've inserted or Tools >> Find in files
You can also select some text while editing a file and search for that in files ;-)

If you have an easier way to achieve this or even add "Search and replace in files" functionality feel free to contribute and i'll update the post.

---

### Post by ruibernardo on 2007-08-29
Thanks ralf57,

it worked perfectly! Very useful, simple and nice. Well done.

---

### Post by ralf57 on 2007-08-30
Glad to know you find it useful

---

### Post by zoopzoop on 2008-03-23
I found a "Regex Search Files" plugin on the Gedit plugins site [http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins) which works better IMO.

---

### Post by ralf57 on 2008-03-25
> **zoopzoop said:**
> I found a "Regex Search Files" plugin on the Gedit plugins site [http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins) which works better IMO.

I haven't tried this plugin, but at least it's less workaround-ish than the solution i posted above

---

