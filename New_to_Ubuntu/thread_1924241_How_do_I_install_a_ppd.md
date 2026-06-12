---
title: "How do I install a ppd"
date: 2012-02-12
forum: New to Ubuntu
---

### Post by joetait on 2012-02-12
I am trying to get my Canon PIXMA MP630 printer working. I found a very useful blog at [http://mp610.blogspot.com/2009/01/new-mp620-and-mp630-printers-ppds.html](http://mp610.blogspot.com/2009/01/new-mp620-and-mp630-printers-ppds.html)

The printer works except that it insists on using the rear tray. In the blog post are links to some files to download. The read me says to do the following:
> 
- For MP600 or MP610 : install Canonâ€™s driver for MP600 or MP610
- For MP620 or MP630 : install Canonâ€™s driver for MP610
- Copy the ppd file (printer/language) along with other ppd files in:
  /usr/share/cups/model/    (Canon driver in rpm package) 
  or: 
  /usr/share/ppd/           (Canon driver in deb package)
- Copy the cifmp600.conf or cifmp610.conf file to replace Canonâ€™s original file in /usr/lib/bjlib/
- Reinstall printer, use the new MP600, MP610, MP620, MP630 printer device provided by .ppd file


The blog post is quite old, so I don;t know if directory locations might have been changed - /usr/share/ppd has no other files .ppd files in it, which I think the above reads as though it should.

And with regards to the .conf file, the directory doesn't even exist. Does anyone know where I should put these files, and if I have to do anything to the files, or just put them where it said?

Thanks

---

### Post by westie457 on 2012-02-12
Have you tried this newer one?

[http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html](http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html)

---

### Post by joetait on 2012-02-12
That worked perfectly, thank you very much :)

---

