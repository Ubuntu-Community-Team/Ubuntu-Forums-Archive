---
title: "create html elements with fixed width using XSLT"
date: 2008-01-29
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-01-29
Hi,

I have a table that shows some text from the database. The I have defined a fixed width for all elements and table with CSS. But, if one of the element has all letters connected like this ggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggg

it will break everything and becomes very big. 

I'm using xslt to transfer my xml document to html, but I don't know if there is any function that can solve this problem.

I really appreciate you spending your time reading this.

Thanks in advance.

---

### Post by BillDozer on 2008-01-29
Check this [http://www.quirksmode.org/css/overflow.html]("http://www.quirksmode.org/css/overflow.html").

---

### Post by mohtasham1983 on 2008-01-29
thanks, but it didn't work. I believe there should be a way to do it in xslt.

---

### Post by BillDozer on 2008-01-29
XSLT converts your to HTML. You should add an attribute to your TD tag (if it is a HTML-table you are creating).
```
<td style="overflow:hidden">
```

---

