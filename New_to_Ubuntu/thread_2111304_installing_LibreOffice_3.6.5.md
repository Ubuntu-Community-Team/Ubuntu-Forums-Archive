---
title: "installing LibreOffice 3.6.5"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by aspergerian on 2013-02-01
LibreOffice 3.6.5 fixes many bugs.
[https://wiki.documentfoundation.org/Releases/3.6.5/RC2#List_of_fixed_bugs](https://wiki.documentfoundation.org/Releases/3.6.5/RC2#List_of_fixed_bugs)

I don't have full LO installed. Is there a safe but thorough way to uninstall such LO components as my computer has so that I can do a clean install of the new LO?

---

### Post by ajgreeny on 2013-02-01
I suggest you install synaptic package manager and use that to search for all libreoffice packages you already have installed, then using the left hand pane choose "status" button and you can select all autoremovable packages.

That should work, I think.  Synaptic is the best package manager available for any *ubuntu OS, in my opinion.

---

### Post by gifford on 2013-02-01
I agree about using Synaptic. If you are not too set on installing LibreOffice 3.6.5, you might wait a week or so to get LibreOffice 4.0.when it is released.

---

### Post by aspergerian on 2013-02-01
Thanks for the suggestions. Synaptic Package Manager seems to have loaded with Xubuntu 12.04.1. I'll wait for LO 4.0

"Version 4.0 is scheduled for release on 10 February 2013."
[http://en.wikipedia.org/wiki/LibreOffice](http://en.wikipedia.org/wiki/LibreOffice)

---

### Post by monkeybrain2012 on 2013-02-01
> **aspergerian said:**
> LibreOffice 3.6.5 fixes many bugs.
[https://wiki.documentfoundation.org/Releases/3.6.5/RC2#List_of_fixed_bugs](https://wiki.documentfoundation.org/Releases/3.6.5/RC2#List_of_fixed_bugs)

I don't have full LO installed. Is there a safe but thorough way to uninstall such LO components as my computer has so that I can do a clean install of the new LO?

Synaptic is good, but for LO there are many packages, it is more convenient to use the terminal then to search for them one by one and mark the checkboxes, a single command
will do.

```
sudo apt-get autoremove libreoffice*
```

---

### Post by aspergerian on 2013-02-02
I seem to have installed LO 3.6.5 on my Acer 1410 running Xubuntu 12.04.1, 64 bit, 4g ram.

I used
sudo apt-get remove 'libreoffice*'
[thnx Paddy]

Then from [http://handytutorial.com/install-lib...u-12-04-12-10/](http://handytutorial.com/install-lib...u-12-04-12-10/)
I used:
sudo add-apt-repository ppa:libreoffice/libreoffice-3-6
sudo apt-get update
sudo apt-get install libreoffice

Thnx to all who responded.

---

