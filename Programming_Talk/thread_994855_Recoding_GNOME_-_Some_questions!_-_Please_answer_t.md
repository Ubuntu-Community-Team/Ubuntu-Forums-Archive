---
title: "Recoding GNOME - Some questions! - Please answer them!"
date: 2008-11-27
forum: Programming Talk
---

### Post by Panarchy on 2008-11-27
Hi

Going to recode GNOME to add a new menu button at the top (Currently: Applications|Places|System).

My questions are;

[LIST=1][*]What compiler should I use for this?

[*]How do I put GNOME 'back' into my custom Ubuntu LiveCD?[/LIST]

Please reply

Thanks in advance,

Panarchy

PS: Any other advice with how to do this will also be appreciated. The files are gnome-main-menu and (maybe) gnome-panel.

---

### Post by nvteighen on 2008-11-27
I'm almost sure you don't have to fiddle with GNOME's source code, but look into some configuration files...

EDIT: Actually you don't even need that. Right-click on panel and select "Edit menus". There you have the "New menu" button!

---

### Post by Panarchy on 2008-11-28
^Thanks... but the option is not there.

What I am trying to do is;

**Add another 'menu' to the top GNOME 'menubar'.**

(A fourth one, next to: Applications|Places|System)

Please help me figure this out.

Thanks in advance,

Panarchy

---

### Post by bruce89 on 2008-11-28
What do you want this menu to have? If it's just launchers, a "drawer" applet would do this.

---

### Post by Panarchy on 2008-11-29
No, I want more than just a drawer applet.

I wish to create a whole 'nother menu at the top menubar.

Please tell me what compiler I should use for this, and how to put my changes back into my custom Ubuntu LiveCD.

Thanks in advance,

Panarchy

---

### Post by nvteighen on 2008-11-29
> **Panarchy said:**
> No, I want more than just a drawer applet.

I wish to create a whole 'nother menu at the top menubar.

Please tell me what compiler I should use for this, and how to put my changes back into my custom Ubuntu LiveCD.

Thanks in advance,

Panarchy
Well, GNOME is written in C, so the compiler will be gcc, as usual. But surely there is some Makefile to automate the process (as there are a lot of source files to compile). Also, you'll have to install your custom GNOME over the default one... Check if you have some way to generate a .deb from the source.

---

### Post by kknd on 2008-11-29
GNOME is very modular, you just need to modify the gnome-panel program. Then recompile just it and install it over the default.

---

### Post by Panarchy on 2008-11-29
^Thanks, but how do I do that?

(Not asking for help with the programming... just with putting the customisations I make to the GNOME source code a] Back into GNOME; then b] Back into Ubuntu)

Please reply,

Thanks in advance,

> **nvteighen said:**
> Well, GNOME is written in C, so the compiler will be gcc, as usual. But surely there is some Makefile to automate the process (as there are a lot of source files to compile). Also, you'll have to install your custom GNOME over the default one... Check if you have some way to generate a .deb from the source.

Hmm... so should I use some gcc frontend? Like CodeBlocks or something? (Also see my other comment... about source code)

Thanks (in advance),

Panarchy

---

### Post by wmcbrine on 2008-11-30
.

---

### Post by Panarchy on 2008-12-02
I'm sorry... what???

:???

Please help me with doing this.

Thanks in advance,

Panarchy

---

### Post by the yawner on 2008-12-02
> **kknd said:**
> GNOME is very modular, you just need to modify the gnome-panel program. Then recompile just it and install it over the default.
I think it would be more specific to try and understand how the applet Menu Bar works. I'm not sure which package it is though. Look into that and find the source code.

Hope that helps.

---

