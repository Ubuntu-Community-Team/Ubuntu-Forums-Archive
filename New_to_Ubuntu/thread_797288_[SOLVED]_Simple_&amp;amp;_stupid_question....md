---
title: "[SOLVED] Simple &amp;amp; stupid question..."
date: 2008-05-17
forum: New to Ubuntu
---

### Post by aberadam on 2008-05-17
I just tried to install Truecrypt.  Double clicked on the .deb package, it says it installed, but can't find it any menu...

Any ideas?

---

### Post by Xiong Chiamiov on 2008-05-17
Some things don't get put in the menu for some strange reason.  Try pressing alt+f2 and running
```

truecrypt

```
Also, you can search for it in synaptic, and see somehow where it is installed to. [goes to look]

EDIT: right-click -> properties -> installed files

---

### Post by aberadam on 2008-05-17
Thanks.  It Runs with Alt + F2 and shows up in Synaptic as well.  

Installed here:

/.
/usr
/usr/bin
/usr/bin/truecrypt
/usr/share
/usr/share/truecrypt
/usr/share/truecrypt/doc
/usr/share/truecrypt/doc/License.txt
/usr/share/truecrypt/doc/TrueCrypt User Guide.pdf

It's working but I'd like it in the Applications menu.

---

### Post by Xiong Chiamiov on 2008-05-17
You can add an entry in your apps menu by following [this]("http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html").  The command you'll be launching will be truecrypt.

---

### Post by aberadam on 2008-05-17
Ahh, I went to the main menu thing in Preferences and added it.  Sorted.  

Thanks for your help.

---

### Post by aberadam on 2008-05-17
Hehe, simultaneous.

---

### Post by hyper_ch on 2008-05-17
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

