---
title: "Apache access.log /var/www/_layout"
date: 2014-02-03
forum: New to Ubuntu
---

### Post by Frank P on 2014-02-03
my log is filled with the error msg "file does not exist /var/www/_layout". It's a test site - not open to the outside world.
What is _layout?  How do I fix the error ?
Thanks
Frank Polan

---

### Post by spjackson on 2014-02-04
This almost certainly means that one (or more) of your pages is referencing that file, perhaps as the name of an image, or more likely a stylesheet. What you need to do is either correct that reference or remove it. It isn't really practical to give detailed instructions of how to do this, since the site might be static html pages or generated dynamically with php or something else. Does the site have any similar filenames, e.g. default_layout.css?

---

### Post by Frank P on 2014-02-04
Okay, I'll keep looking but I'm sure I didn't "deliberately" name a file _layout:(
Thanks
Frank

---

