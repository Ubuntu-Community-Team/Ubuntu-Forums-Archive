---
title: "How to modify &amp; save sources.list"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by NMoawad on 2012-07-10
I am new with Ubuntu and I want to install the Graph tool for python 
[http://projects.skewed.de/graph-tool/wiki/GraphToolDownload](http://projects.skewed.de/graph-tool/wiki/GraphToolDownload)
I followed all the steps of modifying and saving the sources.list , but every time I have this error
 Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

plz I need your help

---

### Post by nothingspecial on 2012-07-10
Question moved to it's own thread.

---

### Post by codemaniac on 2012-07-10
> **NMoawad said:**
> I am new with Ubuntu and I want to install the Graph tool for python 
[http://projects.skewed.de/graph-tool/wiki/GraphToolDownload](http://projects.skewed.de/graph-tool/wiki/GraphToolDownload)
I followed all the steps of modifying and saving the sources.list , but every time I have this error
 Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

plz I need your help

If you are using Ubuntu 12.04 , you will need the below lines appended in your sources.lst .

```
deb http://downloads.skewed.de/apt/precise precise universe
deb-src http://downloads.skewed.de/apt/precise precise universe
```


Please note you need to run 
```
sudo apt-get install graph-tool
```instead of 
```
apt-get install graph-tool
``` .

---

### Post by Paqman on 2012-07-10
I wouldn't edit sources.list manually. Open up Software Sources and put the relevant lines:
```
deb http://downloads.skewed.de/apt/precise
precise
universe
``` into the relevant fields.

If you're not using 12.04 change the "precise" to the correct one for your version (eg: 11.10 = oneiric).

---

### Post by NMoawad on 2012-07-10
unfortunately non of the solutions run 
my ubuntu is 11.04 
any other advices ?

---

### Post by cortman on 2012-07-10
> **NMoawad said:**
> unfortunately non of the solutions run 
my ubuntu is 11.04 
any other advices ?

You should have specified which version you have in the beginning.
Just substitute "natty" for "precise" in Paqman or Codemaniac's instructions.

---

### Post by NMoawad on 2012-07-10
Thank you very much , 
it's finally works , and sorry for bothering you but it's my first time to use Ubuntu

---

### Post by cortman on 2012-07-10
> **NMoawad said:**
> Thank you very much , 
it's finally works , and sorry for bothering you but it's my first time to use Ubuntu

No bother at all- that's what these forums exist for, and that's why we hang out here. :)
Glad to hear it's working- please mark the thread [SOLVED] using the thread tools in the upper right. Good luck!

---

