---
title: "Program doesn't shown in the menu"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by Alex.C on 2011-09-16
Hello,
I've just installed Okular (pdf reader) in Lubuntu through Synaptics package manager but i can't find it listed in the menu (Start>productivity...).

I'm only able to start Okular through the Terminal or Run.

Is there any way i can place it on the start menu or to create a shortcut in the desktop? The problem in that i'm not yet familiarized with the directories and i don't know where is it installed...

Thanks in advance!:)

---

### Post by aeiah on 2011-09-16
have a look here:
[http://wiki.lxde.org/en/Main_Menu](http://wiki.lxde.org/en/Main_Menu)

it says there's no graphical way of editing the menu. that isnt to say the menu doesn't automatically add new items - it may be that this particular program of yours doesn't create the required .desktop file

just as a note, when it says 'open as root', launch it with gksu, eg:
```

gksu leafpad /usr/local/share/applications/your-program.desktop

```

---

### Post by whatthefunk on 2011-09-16
Check the .desktop file in /usr/share/applications/  Its probably called okular.desktop.  Open it up and post what it says here.  You can probably get it to show in the menu with a few simple tweeks.

Note:  To open the .desktop file with the gui, open the file manager and type /usr/share/applications in the address bar.  Find the file, right click, and open it in leafpad.

---

### Post by Alex.C on 2011-09-16
I'll check it! 
Thank you both!

---

### Post by gmargo on 2011-09-16
**Okular** appears in the **lubuntu** (or **lxde**) menu in two places: under _Menu->Graphics->Okular_ and also under _Menu->Office->Okular_.

If you don't see those entries, you can force regeneration of the menu by removing the cached menu file(s) under $HOME/.cache/menus/, then either a) kill and restart **lxpanel**, or b) just log out and back in.

---

### Post by Alex.C on 2011-09-16
> **gmargo said:**
> **Okular** appears in the **lubuntu** (or **lxde**) menu in two places: under _Menu->Graphics->Okular_ and also under _Menu->Office->Okular_.

If you don't see those entries, you can force regeneration of the menu by removing the cached menu file(s) under $HOME/.cache/menus/, then either a) kill and restart **lxpanel**, or b) just log out and back in.

Worked flawlessly! Thanks:)

---

### Post by Alex.C on 2011-09-16
How can i add [SOLVED] to the tilte?

(already done, thanks)

---

