---
title: "How to install Kate editor in gnome"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Louis de Broglie on 2008-09-08
Hi,

I would like to know how to install kate in gnome. I am running ubuntu 8.04 -64 bit hardy :)

---

### Post by philinux on 2008-09-08
sudo apt-get install kate

or use synaptic package manager if you prefer a gui.

---

### Post by billgoldberg on 2008-09-08
> **philinux said:**
> sudo apt-get install kate

or use synaptic package manager if you prefer a gui.

Or use gnome-app-install (applications -> add/remove).

---

### Post by Louis de Broglie on 2008-09-08
Thanks. I installed it from synaptic. But I can't find Kate in applications menu.:confused:

---

### Post by philinux on 2008-09-08
It appears in Applications> Other menu.

---

### Post by Louis de Broglie on 2008-09-08
I find no "Others" sections in Applications.:confused:

However, i tried right clicking on a text file and select other application to run it and i found kate there and i selected kate as default launcher. But nothing launches . Do I need a reboot ? :)

---

### Post by philinux on 2008-09-08
Got to system>prefs and choose Main Menu.

Tick Others to show this sub menu.

It launches fine for me from there. Or in terminal type kate.

No reboot should be necessary.

---

### Post by Louis de Broglie on 2008-09-08
I managed to run kate from the terminal. But the other trick failed . I would like to load kate from Programming sub-menu. I see add-item button there. So how do I link the executable in the programming sub-menu ? :) ( Just like adding programs in start menu in windows )

---

### Post by philinux on 2008-09-08
Yes add item and the executable command 

```
kate --use %U
```

Thats weird it's not running from Other though it works fine here.

When you installed it from synaptic it would have needed to install some other stuff if this was your first kde app. You should have selected Mark for these additional libs etc.

---

### Post by Louis de Broglie on 2008-09-08
This is my first kde app and kate actually is not working properly. For example, if I click on the terminal in lower part of kate window. And empty page appears. :confused:

This is the screenshot of kate : 

[http://i35.tinypic.com/zwetep.png](http://i35.tinypic.com/zwetep.png)

I marked all the packages synaptic asked me to install when i ticked kate.

---

### Post by philinux on 2008-09-08
I'd go to synaptic and mark kate for complete removal. Then install it again. 

Are you using kate or kate-kde4?

---

### Post by philinux on 2008-09-08
Kate is probably looking for Konsole the kde terminal. Maybe thats why the button dont work.

---

### Post by tangibleorange on 2008-09-08
i'm afraid a lot of KDE apps run with bugs like that in GNOME and the same for GNOME apps in KDE. it's just something you've gotta get used to :S

---

### Post by Louis de Broglie on 2008-09-08
I am using Kate not kate of kde4.

---

### Post by tangibleorange on 2008-09-09
try installing kde-core - it improves compatability with a lot of KDE apps, but adds quite a lot of bulk to a system:

```
sudo apt-get install kde-core
```

---

### Post by piyush.rohan on 2011-09-07
try installing konsole:
sudo apt-get install konsole
it is the default kde terminal,then try to install kate

---

