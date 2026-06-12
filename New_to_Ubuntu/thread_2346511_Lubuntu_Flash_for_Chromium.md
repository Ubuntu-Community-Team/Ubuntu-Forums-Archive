---
title: "Lubuntu Flash for Chromium"
date: 2016-12-15
forum: New to Ubuntu
---

### Post by rdb3 on 2016-12-15
Has anyone had success installing the flash plugin for Chromium in Lubuntu?
I am interested in knowing how to do it.  Thanks

Lubuntu 16.04

---

### Post by ajgreeny on 2016-12-15
Enable the **canonical partner** repos in your software-sources and then install **adobe-flashplugin** package.

That should do it.

---

### Post by rdb3 on 2016-12-15
Yes, that did it.  Thanks very much.

I didn't have a problem installing flash on Chromium on my Ubuntu 16.04 partition, but for some reason I ran into some difficulty on the Lubuntu partition.
Anyway, when I just installed via terminal a minute ago, I see that the process removed flashplugin-installer and installed the NEW package...   adobe-flash-properties-gtk adobe-flashplugin.

I went to test the install at [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) and it says that I have Version 24.0.0.186 installed.

---

