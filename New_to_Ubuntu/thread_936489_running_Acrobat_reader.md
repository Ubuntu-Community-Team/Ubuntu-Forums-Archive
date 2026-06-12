---
title: "running Acrobat reader"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by bu2971x on 2008-10-02
I downloaded the linux acrobat from the adobe sight...it is in my downloaded lists...
what is the process for getting it running  from there..??

---

### Post by bigdee973 on 2008-10-02
do you need it to just read pdf files if so you dont need adobe reader just double click a pdf file and it will read pdf files using envince document viewer

---

### Post by SuperSonic4 on 2008-10-02
What's it's file extension? Usally you'd cd to the directory, make it exectuable and run. Assuming it's on the desktop and the file is called file.bin#

```
cd ~/Desktop
```
```
chmod +x file.bin
```
```
./file.bin
```

Before that you could try

[I]"
View and fill in PDF forms online with Adobe Reader and it's browser plugins:"[/I]

```
sudo apt-get remove mozplugger && sudo apt-get install acroread acroread-plugins mozilla-acroread
```

Source: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by bu2971x on 2008-10-02
the file type is rpm
and acroread doesnt work

---

### Post by SuperSonic4 on 2008-10-02
rpm? That's an executable for Red Hat/Mandriva/SUSE

You might be able to use alien to convert it to deb (for debian based systems) but was it available as a deb?

---

### Post by 3rdalbum on 2008-10-03
Add the Medibuntu repository using the instructions here: [www.medibuntu.org](www.medibuntu.org)

Now use Synaptic Package Manager to install the package "acroread". After the package is installed, it will appear in your Applications menu.

Don't download Acrobat Reader from Adobe's site. Adobe doesn't make an easy-to-use installer for Ubuntu.

---

### Post by Kaseas on 2008-10-03
Try following [this tutorial.]("http://www.red91.com/2008/09/22/acrobat-reader-for-ubuntu-hardy")

Although you don't need acrobat reader to view pdf files, the default viewer does just fine.

---

### Post by sonu 1807 on 2008-10-03
I am a newbie myself. First of all you do not need Acrobat reader for viewing pdf files. It can be viewed using the default viewer but if you still need it then go to [http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html). Under select a linux installer select Linux- x86 (.deb) package and then simply download. Synaptic package manager will do the rest.

---

