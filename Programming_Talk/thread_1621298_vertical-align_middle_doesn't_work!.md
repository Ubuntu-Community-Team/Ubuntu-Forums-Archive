---
title: "vertical-align: middle doesn't work!"
date: 2010-11-14
forum: Programming Talk
---

### Post by DanDude on 2010-11-14
Hi!

This is my code:
```
div.subject {
-webkit-border-radius: 15px;
-moz-border-radius: 15px;
border-radius: 15px;
margin-top: 10px;
margin-bottom: 10px;
font-family:"Helvetica", sans-serif;
width:150px;
height:40px;
color:#3dbeff;
background:#ffffff;
text-align: center;
vertical-align: middle;
cursor:pointer;
margin-left: auto;
margin-right: auto;
}
```Still, the text will not be vertically aligned. The div is inside a table, would that matter?

Thanks!
Dan

---

### Post by gmargo on 2010-11-14
Not positive, but I think that **vertical-align** applies only to inline elements, but **DIV** is a block element.

[http://htmlhelp.com/reference/css/text/vertical-align.html](http://htmlhelp.com/reference/css/text/vertical-align.html)

Try applying vertical-align on the **td** cell element in the table.

---

### Post by DanDude on 2010-11-14
Uhm, that won't work.
If I do so, all of the content inside the td will be centered, not the text inside every div...

Thanks!

---

### Post by DanDude on 2010-11-19
Anyone?

---

