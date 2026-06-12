---
title: "HOWTO: pdf/postscript thumbnails in Nautilus"
date: 2005-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by minio on 2005-04-15
It's easy.
 Download [this](http://www.burtonini.com/debian/experimental/pdf-thumbnailer_0.1-1_all.deb) package (you must right click and Save As...)  and install it (sudo dpkg -i pdf-thumbnailer_0.1-1_all.deb). 
Then log out and then log in. 
Now if you open folder with pdf/postscript files you should see thumbnail of the first page of file instead of icon  :grin: 
I've foud this package by chance on internet and i think that more people could find it useful  :)
notice: It doesn't work for some pdf files

---

### Post by ow50 on 2005-04-16
There's also a [Nautilus Thumbnailers](http://www.flyn.org/projects/nautilus_thumbnailers/index.html), which thumbnails among others PDFs and PSs. It is kinda slow though.

---

### Post by minio on 2005-04-16
if you add "-dFirstPage=1 -dLastPage=1" in gs parameters in script gs-thumbnailer from Nautilus thumbnailers should make rendering faster. Parameter force gs to render only first page otherwise it renders whole document.

---

### Post by fitheach on 2005-04-16
Well, I just installed gpdf and evince and also got nice thumbnails, does the tool you mentioned something different?

Regards,
Oliver

---

### Post by Antman on 2005-04-16
[QUOTE=minio]It's easy.
 Download [this](http://www.burtonini.com/debian/experimental/pdf-thumbnailer_0.1-1_all.deb) package (you must right click and Save As...)  and install it (sudo dpkg -i pdf-thumbnailer_0.1-1_all.deb). 
Then log out and then log in. 
Now if you open folder with pdf/postscript files you should see thumbnail of the first page of file instead of icon  :grin: 
I've foud this package by chance on internet and i think that more people could find it useful  :)
notice: It doesn't work for some pdf files[/QUOTE]

Nice tip, thanks.

Ant

---

### Post by minio on 2005-04-16
[QUOTE=fitheach]Well, I just installed gpdf and evince and also got nice thumbnails, does the tool you mentioned something different?

Regards,
Oliver[/QUOTE]
No but it works in deafult Ubuntu instalation.

---

### Post by Bob D. on 2005-04-16
Sweet! Works very well. Nice find...thanks for sharing! 

Bob

---

