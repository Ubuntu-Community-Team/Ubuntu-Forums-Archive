---
title: "Quick question regarding theming"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by timbounceback on 2008-09-29
Hey, could anyone tell me how to change the brown colour when dragging the cursor over the desktop and when hovering over menu items etc.? Thanks.

---

### Post by raul_ on 2008-09-29
You could start by looking in [http://gnome-look.org]("http://gnome-look.org") for another GTK theme you like.

As far as editing your current one, you would have to manually edit the theme file and enter the desired color hex code. But i don't know which fields to change

---

### Post by bruce89 on 2008-09-29
See System>Preferences>Appearence. Most themes can have their colours changed by using the "Customise" button, then going to the "Colours" tab.

---

### Post by timbounceback on 2008-09-29
Thanks for the responses. I already have changed my theme, but unfortunately the theme won't allow me to change the colours.

---

### Post by timbounceback on 2008-09-30
OK, so I've found a version of the theme that allows me to change the colours. Unfortunately, it still won't let me change the menu/file selection colours. Would I have to edit the theme manually for this? If so, could someone give me some pointers?

---

### Post by bruce89 on 2008-09-30
> **timbounceback said:**
> OK, so I've found a version of the theme that allows me to change the colours. Unfortunately, it still won't let me change the menu/file selection colours. Would I have to edit the theme manually for this? If so, could someone give me some pointers?

If a theme doesn't respect the user-defined colours, there's something wrong with it.

Anyway, it'll likely be in ~/.themes. The file to edit is called "gtkrc".

---

### Post by timbounceback on 2008-09-30
Yep, I realise that - I just have no clue where to start! And it's not that it doesn't respect user-defined colours, it's just that it won't allow me to change the colours for the specific things mentioned before (through the GUI, at least).

---

### Post by bruce89 on 2008-09-30
> **timbounceback said:**
> Yep, I realise that - I just have no clue where to start! And it's not that it doesn't respect user-defined colours, it's just that it won't allow me to change the colours for the specific things mentioned before (through the GUI, at least).

Selected menus should be using the "Selected items" colours. If not, that's a bug in the theme. There may be more colours than 8 in a theme, but they are linked to these 8.

---

### Post by timbounceback on 2008-09-30
> **bruce89 said:**
> Selected menus should be using the "Selected items" colours. If not, that's a bug in the theme. There may be more colours than 8 in a theme, but they are linked to these 8.
It's already set as a nice blue-ish colour, so I suppose that would be a bug in the theme?

---

### Post by bruce89 on 2008-09-30
> **timbounceback said:**
> It's already set as a nice blue-ish colour, so I suppose that would be a bug in the theme?

If menus are some other colour, yes. Evidently, some colours are hard-coded, which defeats the purpose of colour themes.

---

### Post by timbounceback on 2008-09-30
> **bruce89 said:**
> If menus are some other colour, yes. Evidently, some colours are hard-coded, which defeats the purpose of colour themes.
Yep, they're brown :-(. So I guess that means I'll have to learn how the gtkrc file works...

---

