---
title: "Python header help!!"
date: 2009-05-29
forum: Programming Talk
---

### Post by iKevin09 on 2009-05-29
checking for a Python interpreter with version >= 2.5... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... /usr/lib/python2.6/dist-packages
checking for python extension module directory... /usr/lib/python2.6/dist-packages
checking for headers required to compile python extensions... not found
configure: error: Could not find Python headers
kevintran@kevintran-desktop:~/blueman-1.10$

This is what I see when I "./configure" Blueman 1.10 so I can use my BlackBerry as a modem. It's not all the text, but just the text at the end that had an affiliation with Python.

The thing is, I don't have Internet on Ubuntu, I do, however have Internet on Windows XP as a dualboot on the same computer.
I want to have a reliable and stable OS, not Microsoft's insanely unstable OS's.

If anybody can help, please, please reply!! This is also in the Networking & Wireless section.

---

### Post by EXCiD3 on 2009-05-29
You should just need the python-dev package to be installed.

---

### Post by iKevin09 on 2009-05-30
> **EXCiD3 said:**
> You should just need the python-dev package to be installed.

How would I get python-dev?

---

### Post by iKevin09 on 2009-05-30
Okay, well I have python-dev installed and the installation continued, but now I need Pyrex. I'm trying to install it, but it's not working out too well..

---

### Post by EXCiD3 on 2009-05-30
sudo apt-get install python-pyrex

Or you can select it from synaptic, should work for you.

---

### Post by iKevin09 on 2009-05-30
Well I didn't have Internet access for Ubuntu to begin with. I was trying to get Internet access to Ubuntu by installing Blueman 1.10, but it turns out that I was trying to install the original blueman 1.10 instead of the Blueman installer package for i386. I downloaded that and it installed beautifully. Now I'm tethered to Ubuntu using my Sprint Blackberry Curve typing up this quick-reply message. I love Ubuntu, never going to re-boot Windows ever again.

---

### Post by EXCiD3 on 2009-05-31
If you've not got internet, check out my project, [Keryx]("http://keryxproject.org").

---

