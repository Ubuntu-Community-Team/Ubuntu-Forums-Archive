---
title: "[Python] ConfigParser doesn't reload my config file"
date: 2010-01-14
forum: Programming Talk
---

### Post by exutable on 2010-01-14
Hey guys,

I am creating a small program where I have a preferences dialog, I want the dialog to save preferences and then have them be reloaded by the main window.  To achieve this I have created a file called arm_prefs.py

arm_prefs.py looks like this
```
import ConfigParser

config = ConfigParser.ConfigParser()
fname = open('config/preferences.conf', 'r')
config.readfp(fname)

def save_preferences():
		fname2 = open('config/preferences.conf', 'w')
		config.write(fname2)
		fname2.close()

def set_preference(cat, sub, text):
	config.set(cat, sub, text)

def get_preference(cat, sub):
	config.readfp(fname)
	return config.get(cat, sub)

```

pretty simple...

Well when my preferences dialog closes and I call get_preference from my main window it still uses the old value UNTIL I restart the program then it gets the correct value.

Any ideas?

---

### Post by exutable on 2010-01-15
I think it has something to do with that pygtk needs to reload that window??? because when I open the preferences window again it has the new values.

Anybody?

---

### Post by exutable on 2010-01-18
Turns out that it was because my init method only runs once meaning that the value from the config file is only read once which is at start-up.

---

