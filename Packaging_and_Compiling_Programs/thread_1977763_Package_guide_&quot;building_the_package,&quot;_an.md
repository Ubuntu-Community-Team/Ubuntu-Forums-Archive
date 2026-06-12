---
title: "Package guide: &quot;building the package,&quot; an enigma."
date: 2012-05-10
forum: Packaging and Compiling Programs
---

### Post by epikvision on 2012-05-10
[http://developer.ubuntu.com/packaging/html/packaging-new-software.html](http://developer.ubuntu.com/packaging/html/packaging-new-software.html) 

I just started on the package guide with renewed vigor until I saw this. Bear in mind I readily followed the steps and codes carefully. The product before this point was 
hello_2.7-0ubuntu1_amd64.build

In the "Building the package" section, however, I typed 
$ lesspipe hello_2.7-0ubuntu1_amd64.deb

and it showed no content.  Then, I typed...
$ sudo dpkg --install hello_2.7-0ubuntu1_amd64.deb

and I got this.  
dpkg-deb: error: `hello_2.7-0ubuntu1_amd64.deb' is not a debian format archive
dpkg: error processing hello_2.7-0ubuntu1_amd64.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 hello_2.7-0ubuntu1_amd64.deb

Can someone tell me what went wrong and why I'm receiving this? Much appreciated.

---

### Post by r-senior on 2012-05-10
Try the next step in the guide, i.e. run Lintian on the .dsc and .deb files.

Lintian should have run as the last step of debuild -- did you notice any errors and warnings?

If running lintian doesn't give any clues, try the debuild step again and post the output.

---

### Post by epikvision on 2012-05-10
Actually, now that I did the page again, I succeeded in having those 2 aforementioned commands work.  There is no problem now. 

Originally, I changed the build-depends text on the control file of the hello/debian folder to the one on the package guide.  Seems that doing so caused an error. On this second try, I left that alone as it was given!  Now it's settled.

Thanks!

---

