---
title: "[SOLVED] {CSS} padding problem"
date: 2008-05-15
forum: Programming Talk
---

### Post by saj0577 on 2008-05-15
I cant seem to get my css file to work so that it has a padding at the bottom.

The padding works when the text on the left hand side is big enough. But when the text on the right hand side is longer it will not extend the black box to cover both parts.

Saj


[http://ubuland.saj0577.co.uk/](http://ubuland.saj0577.co.uk/)


[http://ubuland.saj0577.co.uk/Settings.css](http://ubuland.saj0577.co.uk/Settings.css)

---

### Post by mikemosher on 2008-05-15
saj0577,

Add this to the CSS:

#content_box:after {
    content:".";
    visibility:hidden;
    height:0;
    clear:both;
    display:block;
}

It uses pseudo-classes to fix the issue.  

Good luck. 

Mike

---

### Post by saj0577 on 2008-05-15
Thanks Alot!!!

Saj

---

