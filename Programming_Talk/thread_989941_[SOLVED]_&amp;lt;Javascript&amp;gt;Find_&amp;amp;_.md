---
title: "[SOLVED] &amp;lt;Javascript&amp;gt;Find &amp;amp; replace only partially replacing...."
date: 2008-11-22
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-22
Hello,
In trying to make my website easier to maintain, I used this bit of Javascript for a linkbar:
[PHP]
var identity = 'Home' //This part changes for each page I copy it onto.
var juice='<a href="http://tmac.andrewmin.com/index.html">Home<\/a> | <a href="http://tmac.andrewmin.com/fiddling.html">Fiddling<\/a> | <a href="http://tmac.andrewmin.com/composition.html">Composition<\/a> | <a href="http://python.tmac.andrewmin.com/">Programming<\/a> | <a href="http://tmac.andrewmin.com/writing.html">Writing<\/a>';
document.write(juice.replace(/identity/, '<strong>' + identity + '<\/strong>'));[/PHP]
The idea, of course, is that each time I change something, I only need to change the 'juice' of each page. When it was HTML-ified, it was much more tedious.
However, the output doesn't include any bolding--just a bunch of links. Why?

Thanks.

---

### Post by csilviu on 2008-11-22
Your replace call is trying to replace "identity", which is not in the juice string. 
Just remove slashes:
```
document.write(juice.replace(identity, '<strong>' + identity + '</strong>'));
```

---

### Post by fiddler616 on 2008-11-22
> **csilviu said:**
> Your replace call is trying to replace "identity", which is not in the juice string. 
Just remove slashes:
```
document.write(juice.replace(identity, '<strong>' + identity + '</strong>'));
```
Thanks, that makes sense (just out of curiousity--why slashes and not quotes?)

---

### Post by csilviu on 2008-11-22
regular expressions

---

