---
title: "Pygtk change the default button when a Message Dialog is called"
date: 2010-05-14
forum: Programming Talk
---

### Post by Patagon on 2010-05-14
Hello,

I can change the default button when a Message Dialog is called?:

[PHP]
dialog = gtk.MessageDialog(window, gtk.DIALOG_MODAL,
                                   gtk.MESSAGE_WARNING, gtk.BUTTONS_YES_NO,
                                   "Exit?       ")[/PHP]
 
The default button is "NO", I need to change to "Yes".


Thanks

---

### Post by steeleyuk on 2010-05-14
You just need to add...

```
dialog.set_default_response(gtk.RESPONSE_YES)
```

...before dialog.run() is called.

---

### Post by Patagon on 2010-05-14
> **steeleyuk said:**
> You just need to add...

```
dialog.set_default_response(gtk.RESPONSE_YES)
```

...before dialog.run() is called.


Thanks!

It worked

---

