---
title: "WSGI gives 404 error"
date: 2012-05-04
forum: Programming Talk
---

### Post by Orcris on 2012-05-04
I installed libapache2-mod-wsgi-py3, and activated it in Apache. Now, when I go to localhost, it gives me a 404 not found error. This page worked when I was using CGI, but I get a 404 error with WSGI. Here's what my .htaccess looks like:```
DirectoryIndex index.py index.xhtml index.html
options +ExecCGI
AddHandler wsgi-script .wsgi .py
```How do I fix this error? Right now, I've gone back to using CGI for Python scripts.

---

