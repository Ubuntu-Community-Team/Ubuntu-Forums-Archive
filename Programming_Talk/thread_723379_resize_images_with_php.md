---
title: "resize images with php"
date: 2008-03-13
forum: Programming Talk
---

### Post by tocleora on 2008-03-13
Ok our web site is on shared hosting.  we had imagemagick working but it's since stopped working and because we're on shared hosting we can't fix it, it's been three days and they still haven't fixed it, and our site has a lot of images being uploaded so we desperately need this fixed.  I tried the imagecopyresampled features originally and they would fail to resize if the image was really large (which these are not computer savvy people who are uploading their images straight from their cameras).  I tried graphicmagick but I couldn't get it installed.  This is a linux server but it's not ubuntu so I don't have access to apt-get for example.  any other options?

---

### Post by mssever on 2008-03-13
Have you tried GD?

---

