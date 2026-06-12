---
title: "Python Nautilus Context Menu Extension"
date: 2007-10-13
forum: Programming Talk
---

### Post by TheOz on 2007-10-13
I'm trying to add simple Menu Item into nautilus context menu, with python-nautilus.

But the script seems to don't run. I've placed it into
/usr/lib/nautilus/extensions-1.0/python/ with chmod 755.

```

import gtk
import nautilus
import os

def alert(message):
    """A function to debug"""
    dialog = gtk.MessageDialog(None, gtk.DIALOG_MODAL, gtk.MESSAGE_INFO, gtk.BUTTONS_CLOSE, message)
    dialog.run()
    dialog.destroy()

class TestExtension(nautilus.MenuProvider):
	def __init__(self):
		pass

	def get_file_items(self, window, files):
		items = []
		"""Called when the user selects a file in Nautilus."""
		item = nautilus.MenuItem("NautilusPython::test_item", "Test", "Test")
		item.connect("activate", self.menu_activate_cb, files)
		items.append(item)
		return items

	def menu_activate_cb(self, menu, files):
		"""Called when the user selects the menu."""
		for name in files:
			alert(name)

```

Thanks

---

### Post by WinterWeaver on 2007-10-13
I think you are supposed to have the following on your first line

```
#!/usr/bin/env python
```

if you dont have that line, then you will have to run the script directly with python.

---

### Post by TheOz on 2007-10-13
unfortunatly the solution is not so easier...
the script doesn't run again

---

### Post by macross3003 on 2007-12-30
I'm having the same issue, any solution here?

---

### Post by llonesmiz on 2007-12-31
According to [/usr/share/doc/python-nautilus/examples/README]("file:///usr/share/doc/python-nautilus/examples/README") in order to test your extensions you need to do this:

> To try any of the examples, copy them over to:

    /usr/lib/nautilus/extensions-1.0/python/
or:
    ~/.nautilus/python-extensions/

Then restart nautilus.

Hint: if you're testing an extension that you're developing, it may
be useful to start a 'private' instance of nautilus, like this:
  $ mkdir /tmp/testing
  $ export TMPDIR=/tmp/testing
  $ nautilus --no-desktopThere are some examples in  [/usr/share/doc/python-nautilus/examples/]("file:///usr/share/doc/python-nautilus/examples/") that you could try to modify to suit your needs.

Edit: I've realized that there is a bug in the package "python-nautilus" [https://bugs.launchpad.net/nautilus-python/+bug/145811](https://bugs.launchpad.net/nautilus-python/+bug/145811) . You can download a fixed package from here [https://edge.launchpad.net/%7Ejonner/+archive](https://edge.launchpad.net/%7Ejonner/+archive) (I couldn't install ppa5 but ppa4 works fine).

---

