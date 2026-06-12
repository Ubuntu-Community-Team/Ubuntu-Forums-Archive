---
title: "how to fill a gtkComboBoxEntry"
date: 2007-02-12
forum: Programming Talk
---

### Post by Choad on 2007-02-12
```

weights = ("grams", "kilos", "pounds")

<snip>

def setWeight(self):
		widgets = (self.wTree.get_widget("cmbFrom"), self.wTree.get_widget("cmbTo"))
		for widget in widgets:
			widget.clear()
			# must append values here

```

how would i add the "wieghts" list to each combo box widget?

i've been looking through the documentation, but i cant find anything that works.

---

### Post by duff on 2007-02-12
[http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq16.008.htp](http://www.async.com.br/faq/pygtk/index.py?req=show&file=faq16.008.htp)

---

### Post by Choad on 2007-02-12
hmmm it doesnt seem to work

can you have a look at my project and see whats wrong?

you are supposed to select the unit type from the top combo box, and then the bottom combo boxes are populated with a list

never mind... its fixed (enoguh) for now

---

