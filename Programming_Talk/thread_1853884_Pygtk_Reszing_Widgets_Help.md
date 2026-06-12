---
title: "Pygtk Reszing Widgets Help"
date: 2011-10-03
forum: Programming Talk
---

### Post by possumkeys on 2011-10-03
I've been using pygtk for like a month and each time I create an app of a particular toplevel window size then run the app and maximize it, the widgets also get rescaled and become huge!
Any help on how something simple like a label and a button would retain original size of be neatly dispersed without rescaling?

---

### Post by Smart Viking on 2011-10-03
You'd put the box in a HBox and then in a VBox, or the other way around, and when you pack it into the box you set expand and fill to false, then you use the set_size_request button method.

Or maybe you want to do like gcalctool (gnome calculator) and disable resizing, but that depends on your application.

---

### Post by possumkeys on 2012-01-18
Thanks a lot maen, It did work. #Newbie

---

