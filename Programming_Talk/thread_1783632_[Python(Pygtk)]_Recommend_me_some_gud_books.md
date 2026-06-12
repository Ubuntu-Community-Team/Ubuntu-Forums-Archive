---
title: "[Python(Pygtk)] Recommend me some gud books"
date: 2011-06-16
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-16
hi all,
i am learning Pygtk....so plzzz....recommend some gud books that r explanatory and interesting as well....
if u hv the buk plzz...attach it in ur reply.....

thanks in advance :D

---

### Post by Hairy_Palms on 2011-06-16
[http://zetcode.com/tutorials/pygtktutorial/](http://zetcode.com/tutorials/pygtktutorial/) 
tutorial i used when i first started is there,not so sure on books, but you might want to keep pygobject in mind, as pygtk is deprecated now and wont be updated for gtk3, the syntax is very similar, with a few case changes.

for example in pygtk

```

        self.upButton = gtk.ToolButton(gtk.STOCK_GO_UP);
        self.upButton.set_is_important(True)
        self.upButton.set_sensitive(False)
        toolbar.insert(self.upButton, -1)
```

in pygobject

```

        self.upButton = Gtk.ToolButton()
	self.upButton.set_stock_id(Gtk.STOCK_GO_UP)
        self.upButton.set_is_important(True)
        self.upButton.set_sensitive(False)
        toolbar.insert(self.upButton, -1)
```

---

