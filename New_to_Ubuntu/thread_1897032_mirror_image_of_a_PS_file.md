---
title: "mirror image of a PS file"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by belura on 2011-12-18
I want to get mirror image of a PS file for printing purpose. In debian I could use dvips -o -F -h rev.pro file.ps to get this done. But I find that does not work in Ubuntu. What is the other way?

---

### Post by Palmstroem on 2011-12-18
Since Ubuntu is based on Debian, I cannot see why a rather old and well-known Debian program should not work under Ubuntu.

However, I don't understand your question.

1. Dvips is a program that converts a DVI file (.dvi) to a postscript file (.ps). Where is your DVI file? It should show up in the command line.

2. If your printer does not have a postscript interpreter you nevertheless can print postscript files with a ghostscript driver which nowadays is available for nearly all print devices. When you install your printer under Ubuntu, you will be asked about the driver you wish to install.

3. Maybe the program dvips was simply not installed. Install it by
```
sudo apt-get install dvips
```.

---

