---
title: "GTK Menu Mouse Hover"
date: 2008-09-02
forum: Programming Talk
---

### Post by solarwind on 2008-09-02
Is it just me, or has anyone else noticed that there is absolutely no visual feedback when hovering the mouse over a menubar item? For example, in windows, or even the QT toolkit used by KDE, if you hover your mouse over the "File" menu (just an example), it changes style (glows, changes colour depending on theme, etc...). But I've never seen that with GTK. Is it even possible with GTK?

---

### Post by mssever on 2008-09-02
I don't know if the theme engine supports it, but according to the PyGTK documentation, gtk.Widget supports the enter-notify-event and leave-notify-event signals, which could be used to implement a hover effect.

---

### Post by TheGuyWhoGotOn on 2008-09-03
Offtopic: Wow thanks I was using Tkinter this whole time and PyGTK is to make more Gnome looking apps! Awesome...Time to re-design like the entire interface for some of my apps -.-. BTW solarwind, are you who I think you are? Where did you go? Anyways I'm off to pyGTK tuts.

I've also found the whole visual confirmation over menu-bars weird. However couldn't you change the colour as someone moves the mouse over the item using what mssever said? I know with buttons you get a kinda boarder. Or is this not possible?

---

### Post by solarwind on 2008-09-04
> **TheGuyWhoGotOn said:**
> Offtopic: Wow thanks I was using Tkinter this whole time and PyGTK is to make more Gnome looking apps! Awesome...Time to re-design like the entire interface for some of my apps -.-. BTW solarwind, are you who I think you are? Where did you go? Anyways I'm off to pyGTK tuts.

I've also found the whole visual confirmation over menu-bars weird. However couldn't you change the colour as someone moves the mouse over the item using what mssever said? I know with buttons you get a kinda boarder. Or is this not possible?

Yes, I am the one who you think I am and I was just wondering the same thing about you. RS is dead.

I think this is how GTK is by design as I have never ever seen a visual confirmation on menu mouseover. I absolutely hate that. I hope this gets fixed in GTK 3 and I hope GTK 3 comes out very soon.

---

