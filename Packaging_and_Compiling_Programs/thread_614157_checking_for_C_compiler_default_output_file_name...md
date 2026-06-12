---
title: "checking for C compiler default output file name... configure: error: C compiler"
date: 2007-11-15
forum: Packaging and Compiling Programs
---

### Post by BlanchyUk on 2007-11-15
Hi,
I'm trying to build programs which I've downloaded on the internet, I type:

./configure

and with all of them i get:

checking for C compiler default output file name... configure: error: C compiler cannot create executables

I have the latest Ubuntu and GCC is installed, what am I doing wrong?

---

### Post by patrickfromspain on 2007-11-15
sudo apt-get install build-essential

---

### Post by kumarkrishnan on 2008-05-12
Hi,
  Whether this "sudo apt-get install build-essential" command look for CDROM for installtion or Internet?
  Please reply me. I am trying to install downloaded gstreamer package.
With Thanks,
KK

---

### Post by pedro_orange on 2008-05-13
If you have your CD checked as a repo in your Software Sources tool it should check the CD for the package. 
I know for sure it used to be on the Gutsy CD; not checked Hardy. 

Go for it!

---

### Post by kumarkrishnan on 2008-05-15
Hi,
  I got it installed with CD. 
  Now, I am getting message asking to install gst+- 2.0.0 or above for source code compilation.

With Thanks,
KK.

---

### Post by ad_267 on 2008-05-15
Go to system - administration - synaptic package manager and I think the package it needs is libgstreamer0.10-dev so search for that and install it. If that one doesn't help it may need another package. Search for gst+- or gstreamer and download install the packages with a -dev suffix that look like they may be what you need. Someone else will probably know exactly what package you need.

---

