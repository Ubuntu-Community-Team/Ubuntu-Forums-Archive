---
title: "Chrome and Firefox fail.  IE9 works 100%"
date: 2011-10-17
forum: Programming Talk
---

### Post by bcz on 2011-10-17
Joking of course, but this link shows a problem.  For source see page source in a browser.

[http://mips-erp.com/bug/bug1.php](http://mips-erp.com/bug/bug1.php)


Click to hide all three panes.  Then click to show all three panes.  IE9 works correctly.

Maybe I should use divs, rather than a table, but I found divs were  not doing what I wanted.

Rgds Bill

---

### Post by ve4cib on 2011-10-17
Try adding "float: left;" to the CSS for each panel.  I tried that in Firebug (FF7) and that seemed to do the trick.

---

### Post by bcz on 2011-10-17
All 3 browsers work with CSS

     td.panel {float: left;}

Solved by following up on reply received within 5 minutes of posting on this forum.

Thanks again

---

