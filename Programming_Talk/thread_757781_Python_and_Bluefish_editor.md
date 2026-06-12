---
title: "Python and Bluefish editor"
date: 2008-04-17
forum: Programming Talk
---

### Post by jis on 2008-04-17
I tried to edit a python program by Bluefish in Gutsy, but it indented text so that the program could not be run (even if it looked okay). I edited further in nano and fixed the indention there. Anybody else have noticed this kind of behavior in Bluefish editor?

---

### Post by LaRoza on 2008-04-17
Isn't Bluefish for (X)HTML?

---

### Post by SanskritFritz on 2008-04-17
> **jis said:**
> I tried to edit a python program by Bluefish in Gutsy, but it indented text so that the program could not be run (even if it looked okay). I edited further in nano and fixed the indention there. Anybody else have noticed this kind of behavior in Bluefish editor?Check the settings for automatic tab or space inserting. I say dont use tabs, as there is no standard for tab witdths, any editor can interpret them differently, and this can screw the python interpreter.

---

### Post by LaRoza on 2008-04-17
Four spaces is standard for Python.

---

### Post by jis on 2008-04-17
LaRoza: It is maed to support many programming languages, including Python, as document types.

SanskritFritz: There is "Use spaces to indent, not tabs" checkbox in editor preferences. I am not sure, if it was checked when I experienced the problem. I hope not. Now it is.

---

### Post by LaRoza on 2008-04-17
> **jis said:**
> LaRoza: It is maed to support many programming languages, including Python, as document types.

SanskritFritz: There is "Use spaces to indent, not tabs" checkbox in editor preferences. I am not sure, if it was checked when I experienced the problem. I hope not. Now it is.

Mixing tabs and spaces causes issues. It is best (IMO) to have all spaces, but all tabs works also.

---

### Post by ryanhaigh on 2008-04-17
I haven't used bluefish for editing python scripts but the editor i do use geany has the ability to convert tabs to spaces, I believe you can even customize the number of spaces. Perhaps bluefish has such a feature?

---

