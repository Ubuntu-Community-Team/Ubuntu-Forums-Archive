---
title: "Firefox"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by mtonsbeek on 2008-05-03
Having been a typical MS user for longer than I can remember, I have kind of got used to the using the back space key (is that really what it is called??) for going back to the previously viewed web page. Is there a way of configuring Firefox to do the same, or is there an equivalent key stroke?
Thanks!

---

### Post by zaussome on 2008-05-03
<ALT>Left

---

### Post by mtonsbeek on 2008-05-03
> **zaussome said:**
> <ALT>Left

Yea! It works!
Is it possible to customise it to a single keystroke?

---

### Post by prshah on 2008-05-03
> **mtonsbeek said:**
>  or is there an equivalent key stroke?
Thanks!

Alt-Left arrow

---

### Post by spupy on 2008-05-03
Type in your address bar:
```
about:config
```
In the search field enter "backspace". Should return only one result. Change the value of the key "browser.backspace_action" to "0". Backspace now works as the "back" button. Shift+Backspace is "forward"

---

### Post by mtonsbeek on 2008-05-04
> **spupy said:**
> Type in your address bar:
```
about:config
```
In the search field enter "backspace". Should return only one result. Change the value of the key "browser.backspace_action" to "0". Backspace now works as the "back" button. Shift+Backspace is "forward"

Thanks, that worked!

---

