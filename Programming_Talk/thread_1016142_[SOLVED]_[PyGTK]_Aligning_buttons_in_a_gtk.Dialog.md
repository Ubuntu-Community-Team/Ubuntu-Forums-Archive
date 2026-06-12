---
title: "[SOLVED] [PyGTK] Aligning buttons in a gtk.Dialog"
date: 2008-12-19
forum: Programming Talk
---

### Post by mssever on 2008-12-19
I'm having trouble gettings buttons in a gtk.Dialog to line up like I want them to. The button area is set up like this:
```
+-------+--------------------------------------+--------+----+
| About | empty label which serves as a spacer | Cancel | OK |
+-------+--------------------------------------+--------+----+
```The dialog has two states. In the initial states, the buttons are really spread out, like the first attached screenshot. Later, the gtk.Entry gets resized, resulting in the button layout in the second screenshot. Notice how the buttons are neatly packed in the second screenshot. How do I make that happen in all cases?

---

### Post by mssever on 2008-12-19
Deleting my manual separator and setting the About button to secondary solved this problem.

---

