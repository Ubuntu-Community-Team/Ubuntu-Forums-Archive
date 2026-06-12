---
title: "Help needed! Very needed..."
date: 2008-09-27
forum: New to Ubuntu
---

### Post by adileader on 2008-09-27
Hello everyone,

I am not really new but I still can't figure out what to do with my printer...It is and Epson Stylus D92. I tried installing the D88 and D68 drivers but the printer prints out just plain papers with nothing on them. What should I do? Thanks a lot...

---

### Post by cotcot on 2008-09-27
You could try the latest (beta) version of gutenprint. See [[COLOR="Red"]here[/COLOR]]("http://www.nabble.com/ANNOUNCE:-Gutenprint-5.2.0-beta2-td16951339.html"). The Epson Stylus D92 is in the list of new added printers.

---

### Post by adileader on 2008-09-27
Ok, but how can I install it?

---

### Post by phidia on 2008-09-27
According to the open printing site [your printer]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_D92") is supported and works perfectly. Check the links at that site for setting your printer up or use the Ubuntu [wiki on printing]("https://help.ubuntu.com/community/Printers").

---

### Post by cotcot on 2008-09-27
> **adileader said:**
> Ok, but how can I install it?

You need to download the .tar file (see [[COLOR="Red"]here[/COLOR]]("http://linux.softpedia.com/progDownload/Gutenprint-Download-112.html")). Go to the folder where you download it and right click on the file. Select 'extract here'. In the extracted file open README in a text editor. It explains how to install.
You will have to compile it.
```
./configure
make
sudo make install
```

Do ```
sudo aptitude install build-essential
``` if do not have done this in the past. It is required to be able to compile from source.

---

