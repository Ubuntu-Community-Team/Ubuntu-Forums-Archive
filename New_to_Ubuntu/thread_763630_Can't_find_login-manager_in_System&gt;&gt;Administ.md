---
title: "Can't find login-manager in System&gt;&gt;Administration&gt;&gt;Login manager"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by kaanstiklix on 2008-04-23
I'm using gutsy and i want to change my login screen.But I can't find the option **System>>Administration>>Login Screen Setup.** on my computer.

Any suggestions?
Thanks in advance.

---

### Post by TeoBigusGeekus on 2008-04-23
I don't remember what it was in Gutsy, but in Hardy it is
System->Administration->Login Window.
Anyway, right click the System menu button and choose Edit Menus. Scroll down to Administration and check the appropriate button on the right.
I only hope it is there...

---

### Post by overdrank on 2008-04-23
> **kaanstiklix said:**
> I'm using gutsy and i want to change my login screen.But I can't find the option **System>>Administration>>Login Screen Setup.** on my computer.

Any suggestions?
Thanks in advance.

HI and do you mean system, administration, login window? :confused:

---

### Post by Joeb454 on 2008-04-23
I think that's what the OP needs, I used it on Gutsy before to change my login window theme :) I believe it was System > Administration > Login Window

---

### Post by kaanstiklix on 2008-04-23
Yes, that's what i meant.. login-window.
Ok, so i've right-clicked the System tab and i've clicked on "edit menus" but each time i try to select login-window, it gets deselected automatically.. :confused:

---

### Post by overdrank on 2008-04-23
> **kaanstiklix said:**
> Yes, that's what i meant.. login-window.
Ok, so i've right-clicked the System tab and i've clicked on "edit menus" but each time i try to select login-window, it gets deselected automatically.. :confused:

Ok try using the alt, F2 keys and use this command ```
gksu /usr/sbin/gdmsetup
```

---

### Post by spiderbatdad on 2008-04-23
To get to login window...Left click...system>>adminstration>>login window>>
Then browse the tabs. "local," has themes..."security," has login options...etc.

---

### Post by kaanstiklix on 2008-04-23
thanks, i ran gdmsetup as root through the terminal and managed to change the login screen but i still can't figure out why i'm not able to add login-window to the menu..

---

### Post by fredEbay on 2008-04-23
Are you running xdm instead of gnome etc,?

Try this- 

open terminal/console window

type sudo gdm (if gnome desktop installed)

in the resulting terminal screen, read the info and or answer yes

click OK in the pop-up which should explain another dm or session has the window

gdm should start, you can login there.


From there, you should be able to switch between that and the previous session - crtl-alt-f6 and crtl-alt-f7 or crtl-alt-f8 if I remember correctly.

Good Luck!

---

### Post by kaanstiklix on 2008-04-23
i am running gnome. typing sudo gdm in the terminal gives me this response
```

gdm[6765]: WARNING: GDM already running. Aborting!
GDM already running. Aborting!
```

ctrl-alt-f6/f7/f8 seem to be working fine. there's no problem in switching between sessions

---

