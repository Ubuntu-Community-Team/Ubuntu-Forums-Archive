---
title: "pygtk and combobox"
date: 2008-10-08
forum: Programming Talk
---

### Post by kuzniarpawel on 2008-10-08
Probably a lame question, but googling around for hours and can't find a solution. I want to display three values per row in combobox (Name, Surname, Number), but receive only two (surname, Number). I don't want to convert values to a single string.



    self.set3column(self.lekbox)
    self.nrprawabox_fill()


  def set3column(self, box):
    box = box
    cell = gtk.CellRendererText()
    box.pack_start(cell, True)
    box.set_attributes(cell, text=0)
    box.set_attributes(cell, text=1)
    box.set_attributes(cell, text=2)

  def nrprawabox_fill(self):
        model = gtk.ListStore(gobject.TYPE_STRING, gobject.TYPE_STRING, gobject.TYPE_INT)
    self.lekbox.set_model(model)
    for x in lekdic.keys():
      model.append(row=(lekdic[x][0], lekdic[x][1], x))

---

