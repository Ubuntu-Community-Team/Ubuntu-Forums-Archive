---
title: "Where is the Ubuntu 8.04 Server Guide ?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by LRT on 2008-05-12
how can i get a copy of the Ubuntu 8.04 Server Guide ([https://help.ubuntu.com/8.04/serverguide/C/index.html]("https://help.ubuntu.com/8.04/serverguide/C/index.html")) in PDF format???

---

### Post by FakeOutdoorsman on 2008-05-12
This won't be a single PDF file, but I can offer you a way to save a local copy of the server guide using wget:
```
wget -m -k -np -w 20 --no-check-certificate https://help.ubuntu.com/8.04/serverguide/C/
```
This may take awhile since I set the -w option to 20 seconds, meaning that wget will wait 20 between requests.  It's easier on the server you are mirroring.

---

### Post by hyper_ch on 2008-05-12
you could use wget or httrack to create a local mirror of that (as FakeOutdoorsman already points out)

---

### Post by LRT on 2008-05-13
thanks!

i also found a package called htmldoc ([http://www.easysw.com/htmldoc/](http://www.easysw.com/htmldoc/)) that will convert html to pdf. 

although i was hoping there was already an official pdf somewhere.

---

