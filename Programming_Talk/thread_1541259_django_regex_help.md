---
title: "django regex help"
date: 2010-07-28
forum: Programming Talk
---

### Post by samijam on 2010-07-28
i'm trying to load [http://mysite/blog/2010/jul/28/lorem-ipsum/](http://mysite/blog/2010/jul/28/lorem-ipsum/) on my django site and I'm getting this error about it not matching any patterns:

 > Django tried these URL patterns, in this order:
^themes/(?P<path>.*)$
^admin/doc/
^admin/
^blog/ (?P<year>\d{4})/(?P<month>[a-z]{3})/(?P<day>w{1,2})/(?P<slug>[-w]+)/$
^blog/ ^(?P<year>\d{4})/(?P<month>[a-z]{3})/(?P<day>w{1,2})/(?P<slug>[-w]+)/$
^blog/ ^(?P<year>\d{4})/(?P<month>[a-z]{3})/(?P<day>w{1,2})/$
^blog/ ^(?P<year>\d{4})/(?P<month>[a-z]{3})/$
^blog/ ^(?P<year>\d{4})/$
^blog/ ^$
^tags/(?P<slug>[a-zA-Z0-9_.-]+)/$
The current URL, blog/2010/jul/28/lorem-ipsum/, didn't match any of these.

Shouldn't that first blog url pattern work?

---

### Post by samijam on 2010-07-29
^blog/ (?P<year>\d{4})/(?P<month>[a-z]{3})/(?P<day>w{1,2})/(?P<slug>[-w]+)/$

should have been:


^blog/ (?P<year>\d{4})/(?P<month>[a-z]{3})/(?P<day>\d{1,2})/(?P<slug>[-\d\w]+)/$

---

