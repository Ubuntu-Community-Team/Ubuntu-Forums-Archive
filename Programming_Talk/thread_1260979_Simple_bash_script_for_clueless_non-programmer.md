---
title: "Simple bash script for clueless non-programmer"
date: 2009-09-08
forum: Programming Talk
---

### Post by taslinux on 2009-09-08
This forum post explains what I want:

[http://ubuntuforums.org/showthread.php?p=7864353](http://ubuntuforums.org/showthread.php?p=7864353)

To get there I'd like to associate plain text documents with an 'if-else' bash script conditional on the filename, something like if it's "*.xyz", start special Wine program, else open with gedit.

Any help very welcome.

---

### Post by Linteg on 2009-09-08
I'd recommend you to create a new mime-type for the file extension(s). Then only the files of this specific mime-type will opened by your script. Take a look at [http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-modifying.html.en](http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-modifying.html.en)

---

### Post by taslinux on 2009-09-09
Brilliant! Thanks, Linteg. Very simple and it works perfectly.

---

