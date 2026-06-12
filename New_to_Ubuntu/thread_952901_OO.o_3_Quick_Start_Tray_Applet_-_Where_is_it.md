---
title: "OO.o 3 Quick Start Tray Applet - Where is it?"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by crjackson on 2008-10-19
Since installing OpenOffice 3, I can't find the option to turn on the Quick Start tray icon. Has this been removed or is there a way to get it back?

Hardy 8.04.1 32bit.

---

### Post by gjoellee on 2008-10-19
Do you mean the icons that appear in the menu?

Lets follow the tutorial here: [http://www.kshoster.net/node/56](http://www.kshoster.net/node/56) 

this will make the icons in the Menu appear as well as installing OOo3

---

### Post by crjackson on 2008-10-19
> **gjoellee said:**
> Do you mean the icons that appear in the menu?

Lets follow the tutorial here: [http://www.kshoster.net/node/56](http://www.kshoster.net/node/56) 

this will make the icons in the Menu appear as well as installing OOo3

No, it's installed perfectly. Version 2.4 used to have a quick launcher icon that loaded in the systray (notification area) on boot. When it was present, you could launch writer and other apps faster than without it.

Activation of the quick launcher used to be in TOOLS>OPTIONS>MEMORY area of the settings. It's not there anymore.

---

### Post by roger_1960 on 2008-10-19
Hi

You can drag the icon from the drop down main menu and drop it onto the 'systray'

---

### Post by crjackson on 2008-10-19
> **roger_1960 said:**
> Hi

You can drag the icon from the drop down main menu and drop it onto the 'systray'

What icon are you talking about? The quick launcher let you select any of the OOo applications. I'm not trying to just have a Writer icon to avoid having navigate the menus. The quick launcher actually made the programs start faster (or so it seems).

---

### Post by roger_1960 on 2008-10-19
Hi

Now I understand - didn't know before there was one but found the setting in 'options' , but in 2.4.1.  Dont know in version 3, sorry!

---

### Post by ddarsow on 2008-10-19
I think that a launcher with the following command is what you want:

```
/opt/openoffice.org3/program/soffice
```

Here is the icon if you need it:

[IMG]http://www.ddarsow.com/images/ooo30.png[/IMG]

---

### Post by dbcoolio on 2008-10-20
I believe The quick start tray applet functions as part of the gnome-openoffice integration package, so if you had ooo3 installed separately (ie not through an official repository) then that's why it would have disappeared.

I'm having a different problem, I can get the quickstart tray applet to appear during a session, but it won't load after a restart.  I'm going to try doing some things as root, but I'm not sure how it will all turn out.

---

### Post by crjackson on 2008-10-21
> **dbcoolio said:**
> I believe The quick start tray applet functions as part of the gnome-openoffice integration package, so if you had ooo3 installed separately (ie not through an official repository) then that's why it would have disappeared.

I'm having a different problem, I can get the quickstart tray applet to appear during a session, but it won't load after a restart.  I'm going to try doing some things as root, but I'm not sure how it will all turn out.

Okay, thanks. Let me know what you find out.

---

