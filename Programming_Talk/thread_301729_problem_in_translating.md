---
title: "problem in translating"
date: 2006-11-17
forum: Programming Talk
---

### Post by freemanen on 2006-11-17
I have this code. I have followed a guide and got a .po file with both the glade files string and the string in .py file. I translate the string and make a mo file. Byt then I start the program I just got the translation of string in the .py. why?

```
import gtk.glade
import gettext
import locale


APP = "tjo"
DIR = '/home/ubuntu/hej/locale'
locale.setlocale(locale.LC_ALL, '')

gettext.bindtextdomain(APP, 'locale')
gettext.textdomain(APP)

#locale.setlocale(locale.LC_ALL, '')
#gettext.bindtextdomain(APP, DIR)
#gettext.textdomain(APP)
#gettext.install(APP,DIR)
_=gettext.gettext

class tjo:
	def __init__(self):
		self.window = gtk.glade.XML('hej.glade', 'window1', APP)

if __name__ == '__main__':
	print _('Hello World!')
	tjo()
	gtk.main()
```

---

