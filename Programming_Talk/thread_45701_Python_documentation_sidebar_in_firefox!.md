---
title: "Python documentation sidebar in firefox!"
date: 2005-07-01
forum: Programming Talk
---

### Post by UbuWu on 2005-07-01
Get the python sidebar for firefox:
[http://projects.edgewall.com/python-sidebar/](http://projects.edgewall.com/python-sidebar/)
It helped me very much with starting with python programming...  :grin:

---

### Post by ow50 on 2005-07-01
Works in Epiphany as well.

Other resources:

[Devhelp](http://developer.imendio.com/wiki/Devhelp) to view documentation installed on your hard drive (package python-doc). Usable also for other hard-drive installed documentation, for example PyGTK.

Search bookmarklet to search Python online documentation:
```
javascript:q = '' + (window.getSelection ? window.getSelection() : document.getSelection ? document.getSelection() : document.selection.createRange().text); if (!q) q = prompt('Search Python documentation for:', ''); if (q!=null) location='http://www.google.com/search?domains=docs.python.org&sitesearch=docs.python.org&sourceid=google-search&submit=submit&q=' + escape(q).replace(/ /g, '+'); void 0
```

---

### Post by Mike Buksas on 2005-07-15
Those both look like very handy tools. Thanks for passing them on!

Mike

---

