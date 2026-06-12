---
title: "Python CGI File Upload Question"
date: 2009-08-31
forum: Programming Talk
---

### Post by jeffmikels on 2009-08-31
PHP has a function that allows me to "move_uploaded_file".

Python's cgi module uses StreamIO for uploaded files and therefore requires an expensive "save" operation.

The only time this is a problem is with large files that take a long time to read the data and write it to the filesystem. However, the only reason I'm using python is because of the file size limit imposed by my hosting provider's php.ini.

Simply put, is there a way to speed up the file saving/moving operation of files uploaded to a python cgi script?

---

