---
title: "capturing ESC, page up/down in Python"
date: 2008-10-26
forum: Programming Talk
---

### Post by jordilin on 2008-10-26
Is there any way to capture the keyboard events ESC, page up (next page), page down (previous page) in Python?. I mean, how can I capture if user presses one of those keys in a terminal based application? I was thinking about pygame.key.get_pressed from the pygame module, but I don't feel really happy about importing pygame in a non related game project.

---

### Post by wmcbrine on 2008-10-26
import curses

although curses can be overkill, too. But I don't know a simpler way offhand.

---

### Post by sheto on 2008-10-27
You can try GASP, maybe. Their website is [https://launchpad.net/gasp]("https://launchpad.net/gasp") and it is simple to use. Best of luck!

---

### Post by jordilin on 2008-10-28
Probably I will need to import some graphics library. If I seem to remember java has a KeyListener from awt. I'm still thinking on how to proceed.

---

### Post by wmcbrine on 2008-10-28
No, if it's a terminal app, you should be looking at curses before you resort to anything GUI.

---

