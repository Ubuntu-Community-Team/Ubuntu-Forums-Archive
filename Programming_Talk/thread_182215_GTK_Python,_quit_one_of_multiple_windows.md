---
title: "GTK Python, quit one of multiple windows"
date: 2006-05-25
forum: Programming Talk
---

### Post by Ubuntuud on 2006-05-25
Hi,
I am making a program, with an exit confimation popup. But how can I let just the popup disappear when the user clicks "no". Something like "self.popup.quit()"? With "self.popup" being a "gtk.Window".

Thanks in advance!

---

### Post by dabear on 2006-05-25
gtk.Window should inhert from gtk.Object which has a destroy()-method you could use.

---

### Post by Ubuntuud on 2006-05-25
Offcouse, stupid me, thanks!

---

