---
title: "Cannot Find Software Center Installation of PHP-TCPDF"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by Martin_Corrigan on 2013-11-03
I am working with the standard LAMP web development environment.  I wanted to try the TCPDF extensions to PHP to create PDF files.  In the Ubunto Software Center I found the installation for "php-tcpdf(6.0.010+dfsg-1)".  Following the standard processes in the Software Center, I installed this package.  It shows it installed under the "History" category.  However, I cannot find the libraries or files anywhere on my system.  Does anyone know how to trace where the Software Center has put something that you installed?

---

### Post by sandyd on 2013-11-03
> **Martin_Corrigan said:**
> I am working with the standard LAMP web development environment.  I wanted to try the TCPDF extensions to PHP to create PDF files.  In the Ubunto Software Center I found the installation for "php-tcpdf(6.0.010+dfsg-1)".  Following the standard processes in the Software Center, I installed this package.  It shows it installed under the "History" category.  However, I cannot find the libraries or files anywhere on my system.  Does anyone know how to trace where the Software Center has put something that you installed?

A list of all the files that should be installed
[http://packages.ubuntu.com/saucy/all/php-tcpdf/filelist](http://packages.ubuntu.com/saucy/all/php-tcpdf/filelist)

---

### Post by heir4c on 2013-11-03
Install "Synaptic". Than open it and go to Settings/preferences. Go to the first Tab and check the first line "Display Package Properties in the main window" (or something like that, I have the Dutch version, so I translate that word for word). And click at the bottom "Apply" an than "OK".
After that you search for the packages you want and in the lower window you can see in the 4th Tab where the files are of that packages.


[IMG]http://i.imgur.com/Y7d5sEo.png[/IMG]

---

### Post by heir4c on 2013-11-03
With the command:
```
sudo dpkg --get-selections > list.txt
```
you can create a file of all the installed packages with the name list.txt in your homefolder.

---

