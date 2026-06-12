---
title: "Hi, I'm new. I can't connect my hp1018 printer  It prints a test page but won't print"
date: 2015-06-06
forum: New to Ubuntu
---

### Post by rover2 on 2015-06-06
Hi, I'm new. I can't connect my hp1018 printer  It prints a test page but won't print from office or browser ?
Any help please ?

---

### Post by rover2 on 2015-06-06
Ubuntu 14.4.2 64 bit

---

### Post by Bucky Ball on 2015-06-06
Welcome. Do you have HPLip installed? Find it in the Software Centre. You may need to enable Canonical Partners repository in your Software & Updates (I think it's called in Ubuntu). 

Please give more detail as to how you added/installed the printer. Did you install a driver for it? Network or USB? Wireless? Set up via USB first.

You need to add the printer and correct driver (probably) with 'Printers' or via cups (open a browser and type 'localhost:631' in the address bar).

It should work fine once we get it set up (probably once you add hplip). [Here's]("http://www.hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html") some more info. HP models are usually very Linux friendly so there's a start. Having the right hardware is key to a smooth Ubuntu ride IMHO. ;)

---

### Post by leunam12 on 2015-06-06
From HP Linux imaging and Printing:

"Driver Plugin Information:

This printer REQUIRES a downloadable driver plug-in, which is required to enable print, fax or scan support. Use hp-setup to install the printer, and to download and install the plug-in. Driver plug-ins are released under a proprietary (non-open) license and are not part of the HPLIP tarball release."

What to do? Go to this webpage:

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1018.html)

Click the "Download HPLIP" button, save the file on a separate dedicated folder; then, on the terminal navigate to the folder where you saved the hplip-3.15.4.run file and do: ```
chmod +x hplip-3.15.4.run
```press enter and then do:```
./hplip-3.15.4.run
``` and follow all the interactive directions. I usually say yes to all the defaults (marked with an asterisk in the installation routine). An active internet connection is required since the script is going to download and install plugins and missing dependencies.

---

### Post by Bucky Ball on 2015-06-06
Or install HPLip from the Software Centre ...

Not sure there's a difference, apart from perhaps the version number. If there is, please inform.

---

### Post by leunam12 on 2015-06-06
I don't know if there is a difference, that is how I do it all the time. It installs everything that you need in one step

---

