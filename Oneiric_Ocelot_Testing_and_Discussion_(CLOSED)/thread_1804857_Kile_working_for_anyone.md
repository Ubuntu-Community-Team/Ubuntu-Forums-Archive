---
title: "Kile working for anyone?"
date: 2011-07-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-07-15
Kile crashes here on two systems with

> No editor component found. Please check your KDE installation.

Is it just me or is this a bug?

Edit: Kate seems to crash/krash too. Seems there's an underlying problem.

---

### Post by SevenMachines on 2011-07-15
Same here, i dont use kde but is there a way to set the default text editor? The fallback for
KTextEditor::EditorChooser::editor()
is kate so if you install that it should work after the warning

[EDIT] Sorry, i see you have kate problems, i should pay attention more!

---

### Post by MacUntu on 2011-07-15
I only have Kile and Kate installed, I don't know which other programs to test that don't fill my Ubuntu installation with Krap (sorry, could not resist :D).

Edit:

From IRC:

[QUOTE=yofel] katepart was moved out of kdelibs5-plugins into kate and we're still working on that, so until a new kate package is out all apps that use the katepart as an editor won't work[/QUOTE]

---

### Post by SevenMachines on 2011-07-15
Seems i cant set kde default applications 'kde embedded text editor service' to anything at all let alone kate, maybe thats the bug? kde users may know...

---

