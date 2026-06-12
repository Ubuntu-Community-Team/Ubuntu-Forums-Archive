---
title: "Paint Shop Pro"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by robert1305-gmail on 2014-04-27
I am finding Gimp hard to handle, can anyone tell me if its possible to install PSP in 14.04. and if so how do I do it. ( used it for years in Windows )

Would be very grateful for any suggestions at all for any alternatives to Gimp.

Regards Bob

---

### Post by The Spectre on 2014-04-27
There are quite a few image editors to chose from...
[https://apps.ubuntu.com/cat/department/painting/](https://apps.ubuntu.com/cat/department/painting/)

Both of these are pretty popular...
[https://apps.ubuntu.com/cat/applications/pinta/](https://apps.ubuntu.com/cat/applications/pinta/)

[https://apps.ubuntu.com/cat/applications/krita/](https://apps.ubuntu.com/cat/applications/krita/)


There is even a free Online Image Editor that works pretty well..
[http://pixlr.com/editor/](http://pixlr.com/editor/)


I would recommend giving one of them a try but continue using Gimp until you get over the learning curve of using Gimp.

---

### Post by squakie on 2014-04-27
Something to keep in mind:  PSP is a Windows based program (at least it was the last time I used it years ago).  As such, you'll either need a virtual machine to run some version of Windows in (if your hardware will support it) or wine to run a Windows application.  Wine is not the best choice for several reasons - amongst those being Wine won't run all Windows programs, USB is not available in Wine so if you use a USB drawing tablet, etc., it would not be accessable under Wine.

My suggestion:  

install synaptic package manager via sudo apt-get install synaptic

start synaptic (via the menus)

scroll on the left down to the various "Graphics" catagories

look at the packages available

Depending on what you want to do, there are many packages there including imagemagick and inkscape, plus as The Spectre mentioned there are many others availale from 3rd parties and not directly supported by the makers of Ubuntu.  Try searching the net using:

ubuntu graphics editors

in the search string.

---

