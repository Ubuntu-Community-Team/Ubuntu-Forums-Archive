---
title: "[SOLVED] How do you change Firefox shortcut keys?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by dj_akasha on 2008-06-11
Hi, I've been trying to figure out how to make the backspace button make the window in firefox go back a page like in IE.  I've had a look through the forums but can't find anything.

Any help would be greatly appreciated.  Thanks!

---

### Post by _sphinx_ on 2008-06-11
Actually I don't konw how to change it and I think it may help you to know that "alt+<right arrow>" take you to the previous page.

---

### Post by _sphinx_ on 2008-06-11
Sorry a correction "alt+<left arrow>"...

---

### Post by dj_akasha on 2008-06-11
That's useful thanks!  I hope I remember it 'cos have had too many years with Windows and it's difficult to let go of certain things.

---

### Post by _sphinx_ on 2008-06-11
By the way this shortcut also work in Windows IE and Windows Explorer and Gnome file handler i.e nautilus, and in many more , so it's a kind of universal shortcut for going back and also obiously alt+<right arrow> for coming forward.

---

### Post by gameryoshi600 on 2008-06-11
alt+left key goes back
alt+right key goes forward
esc key will stop the page
ctrl+c keys will copy text if selected
ctrl+a keys will select all
ctrl+v keys will paste
F5 key will refresh

there is more key combos here: [http://support.mozilla.com/en-US/kb/Keyboard+shortcuts](http://support.mozilla.com/en-US/kb/Keyboard+shortcuts)

---

### Post by y-lee on 2008-06-11
> **dj_akasha said:**
> Hi, I've been trying to figure out how to make the backspace button make the window in firefox go back a page like in IE.  I've had a look through the forums but can't find anything.

Any help would be greatly appreciated.  Thanks!

If you really want this feature:

In Firefoxes address bar, type **about:config** now enter the word “backspace” in the filter field, you should now see an entry called  **browser.backspace_action**. Double click on this entry to change the value from 1 to 0.

---

### Post by dj_akasha on 2008-06-12
> **y-lee said:**
> If you really want this feature:

In Firefoxes address bar, type **about:config** now enter the word “backspace” in the filter field, you should now see an entry called  **browser.backspace_action**. Double click on this entry to change the value from 1 to 0.

Fab thanks!  Worked like a charm.

---

