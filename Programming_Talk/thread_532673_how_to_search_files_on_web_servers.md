---
title: "how to search files on web servers"
date: 2007-08-23
forum: Programming Talk
---

### Post by Coder_wannabe on 2007-08-23
Does anyone know of a good way to search through files on a webserver from the web?  For example, if were to go to xyz.com.  How could i search through the file system from the url line?

---

### Post by CptPicard on 2007-08-23
AFAIK, you don't, if the server hasn't been explicitly configured to give you a file listing of directories, which you could parse.

Of course, if we're talking about web pages, you can parse html and recurse to every linked page and file, but it still won't let you browse everything there is... it can be even thought of as a security feature of sorts...

---

### Post by pmasiar on 2007-08-23
If a webserver would allow user to search files outside so called "document root", it would go down in flames and/or got pwned within 15 minutes after going online.

You probably wanted [http://en.wikipedia.org/wiki/Webcrawler](http://en.wikipedia.org/wiki/Webcrawler) ? It can reach only  hyperliked pages, not all files on server.

---

