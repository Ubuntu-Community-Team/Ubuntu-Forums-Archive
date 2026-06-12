---
title: "How to change keyboard layout in Emacs"
date: 2009-12-07
forum: Programming Talk
---

### Post by vuolleko on 2009-12-07
Hi,

This must be trivial, but after spending a few hours googling and reading through the help, I give up. So: how can I change the keyboard layout in Emacs (version 22.2.1 on 64-bit Kubuntu 9.10)?

More specifically, I have a Finnish keyboard on a Dell D430 laptop (it's a slightly modified QWERTY). Many default Emacs bindings are tricky on this one, so I would like to change the layout to the 'American' (or what ever it's called?) I imagine this is a common problem, and indeed, I found the C-x <RET> C-\ command... but even if I choose english-dvorak, it remaps only some of the keys, and the annoying 'ö' letter prevails (which I think should not exist on dvorak, and should give the semicolon on US layout). How do I change the entire keyboard layout?

I don't want to change the keyboard layout in KDE. Nor do I want to create my own bindings, because I want to have a familiar layout everywhere where I ssh to.

Thanks.

---

### Post by vuolleko on 2009-12-15
Anyone? This problem is really annoying; wouldn't want to go back from Emacs... :(

---

### Post by CptPicard on 2009-12-15
Hello, fellow Finn(?) :)

C-x RET C-\ seems to select the input method... so I suppose this probably does not have to do with keybindings. Maybe you could edit one input method or create your own?

---

### Post by vuolleko on 2009-12-16
I could... But the point is that I would like to have the same binding configuration wherever I ssh to.

An alternative would be to have a different keyboard layout for the terminal. But I couldn't find such configuration in the KDE menus. There are lots of application specific settings you can choose from, why not keyboard layout?

---

