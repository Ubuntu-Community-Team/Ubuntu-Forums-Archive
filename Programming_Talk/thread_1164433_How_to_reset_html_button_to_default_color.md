---
title: "How to reset html button to default color"
date: 2009-05-19
forum: Programming Talk
---

### Post by tc101 on 2009-05-19
I have an html button that I turn red , using javascript,  when an action needs to be taken.  I want to set it back to it's default color after the action is taken.  There is nothing in the  style.css that sets it.  Is there some default for html button colors?

---

### Post by odyniec on 2009-05-19
Try setting the color to an empty string:
```
button.style.backgroundColor = '';
```
I'm not sure if it works across all browsers, though.

---

### Post by tc101 on 2009-05-19
That works.  Thanks.  For this project it only needs to work in IE.

---

