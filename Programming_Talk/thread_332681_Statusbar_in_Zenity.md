---
title: "Statusbar in Zenity?"
date: 2007-01-06
forum: Programming Talk
---

### Post by Balaam's Miracle on 2007-01-06
I'm currently cooperating with someone to make a backup script and we are using Zenity to make the dialogs.
But we are now looking for a way to get the status messages that are currently sent to the console, to show up in a status bar or screen.

Does anyone know if this is possible with Zenity and if so, how?

---

### Post by Balaam's Miracle on 2007-01-07
Anybody? Please?

---

### Post by Wybiral on 2007-01-07
I've never been able to get that darn progress bar in zenity to work right, this is the example in "man zenity"

find $HOME -name ’*.ps’ | zenity --progress --pulsate

If you take out the "--pulsate" it should work, but it hasn't ever worked right for me.

---

### Post by Balaam's Miracle on 2007-01-08
Thanks for the reply, but i'm not trying to add a progress bar but a status bar.
You know, a line that shows - in text - the current status of the process. Like "Now copying file 'lalala.txt': no such file" or "Preparing disk 4 of 25".

Currently, the status messages are sent to the console, but we want to have it shown in the GUI.

We may add a progress bar later, but has not a high priority.

---

