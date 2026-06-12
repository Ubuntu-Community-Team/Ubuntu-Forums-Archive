---
title: "[pygtk] close a dialog box"
date: 2008-11-19
forum: Programming Talk
---

### Post by harmankardon on 2008-11-19
Hello

Here is example : 
```
#! /usr/bin/env python
 
import os, gtk
 
def validation():  
	dialog = gtk.MessageDialog(None,0,gtk.MESSAGE_QUESTION,gtk.BUTTONS_OK_CANCEL,'run gedit ?')
	c=dialog.run()  
	dialog.destroy()
	if c == gtk.RESPONSE_OK:
		return 1
	return 0
 
if validation():
	os.system('gedit')
print "it's over"
```

The problem : when I click OK, Gedit starts but the dialog box remains open.

I would like to click OK, at this moment the dialog box closes and Gedit runs. And when i close gedit, the script print "it's over". 
It's possible ?

---

