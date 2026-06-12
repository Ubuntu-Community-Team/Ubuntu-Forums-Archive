---
title: "Gtk2 provide any dialog box option which close automatically on event?"
date: 2016-03-03
forum: Programming Talk
---

### Post by Anes_P_A on 2016-03-03
Dear Friends,
I am using PyGtk for my project. I have a dialog with some combobox listing . Currently it work with an Ok & Cancel button. My requirement is I need to remove the OK and Cancel button and in onchange of Combobox items need to submit that value and automatically close the
dialog without any manual intervention. 
My current code is 

```

def mostrar_combobox(self, titulo, texto_etiqueta, lista):
    """
    MÃ © All to show a combobox on screen and get the option chosen
    """
    #print texto_etiqueta
    #dialogo = gtk.Dialog(titulo, None, 0, (gtk.STOCK_OK, gtk.RESPONSE_OK, gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL))
    dialogo = gtk.Dialog(titulo, None,  gtk.DIALOG_MODAL, None)
    dialogo.connect('response', lambda *x: self.destroy())
    etiqueta = gtk.Label(texto_etiqueta)
    etiqueta.show()
    dialogo.vbox.pack_start(etiqueta)
    combobox = gtk.combo_box_new_text()
    for x in lista:
      combobox.append_text(x)
    combobox.connect('changed', self.changed_cb)
    combobox.show()
    dialogo.vbox.pack_start(combobox, False)
    response = dialogo.run()
    combobox.connect('changed', self.changed_cb)
    dialogo.emit("delete-event", gtk.gdk.Event(gtk.gdk.DELETE))
    elemento_activo = combobox.get_active()
    return elemento_activo
    
 
  def changed_cb(self, combobox):
    index = combobox.get_active()
    if index > -1:
      print index



```

My application dialog preview is :

[ATTACH=CONFIG]267611[/ATTACH]

Waiting for fast reply

Thanks
Anes

---

### Post by Anes_P_A on 2016-03-05
Dear Friends,
I added a new fucntion as :
```

def destroy_dialogo(self): 
    """ 
    MÃ © everything to destroy a window 
    """
    gtk.main_quit() # close all window...
     
    return True

```

but calling it closes entire application. There is any alternative to this to close only the dialogue...
Waiting for fast help

Thanks
Anes

---

