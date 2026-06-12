---
title: "Howto open terminals"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-06-30
In some areas I'm really a n00b. Even though I'm not new to google I seem to be blank on what to search for. I remember a friend of my had set up his terminal so that if he opened more than one they would open under or on the side of the previous one so that when he had opened four terminals they would each be seated in four different corners. Now if I open two terminals the second one open on top of the first one and so on. Which seems very unlogical to me. Is there a way to open terminals in different corners than the previous one. And of course without affecting other programs.

I'm using the default gnome Terminal 2.22.1.

---

### Post by iaculallad on 2008-06-30
That would simply just be pressing the **Ctrl+Shift+T** key combo when you're on a terminal. Pressing the combo would cause your new Terminal window to be "tabbed" next to the first Terminal window.

Don't know if that's what you mean.

EDIT: Missed T, too fast

---

### Post by sayakb on 2008-06-30
At a terminal, press Ctrl+Shift+T to open a new tab.

---

### Post by peakshysteria on 2008-06-30
No thats not it. I want four separate/different terminal windows seated in four different corners of the screen. Each time I open a terminal window it will place itself in the corner which is free (not taken by previous opened terminal). (Not four terminals opened in four tabs in the one and same terminal window).

---

### Post by mevets on 2008-06-30
One way to do this is at the window manager level. If you run compiz, it has a plugin named Place Windows. This plugin manages where windows show up when an app creates a new window. By default, it is set to smart and it will do what you described.

---

### Post by peakshysteria on 2008-06-30
I know. But currently I'm not able to run Compiz. And I would like the feature to be exclusive to the terminal(s) and not interfere with opening other programs.

---

### Post by sayakb on 2008-06-30
This will not help completely I think. Press Alt+F2 and type in [B]gconf-editor
[/B]Navigate to /apps/metacity/general
There, change the value of **focus_new_windows** to **strict**.

---

### Post by peakshysteria on 2008-06-30
Nice. Thanks, it works for two terminal windows. If I'm opening a third and a fourth window the open in top of the window currently *not* in focus. So I'm half way there it seems :) So now, how to make a third and a fourth terminal open in the other corners of the desktop?

---

