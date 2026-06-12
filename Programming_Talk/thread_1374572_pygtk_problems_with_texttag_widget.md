---
title: "pygtk problems with texttag widget"
date: 2010-01-07
forum: Programming Talk
---

### Post by zimio on 2010-01-07
I write this code in my program:

buffer = self.log_textview.get_buffer()
tagtable = buffer.get_tag_table()
tag = tagtable.lookup('comment')
print tag.invisible

And then I get 

AttributeError: 'gtk.TextTag' object has no attribute 'invisible'



But in the documentation it says that it does have that attribute...
[http://www.pygtk.org/docs/pygtk/class-gtktexttag.html](http://www.pygtk.org/docs/pygtk/class-gtktexttag.html)

What's the problem?

Thanks in advance.

---

