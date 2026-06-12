---
title: "Installing printer files"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by kelcie234 on 2008-04-24
I am trying to install the lexmark z605 by following this guide:


[http://ubuntuforums.org/showthread.php?t=83456](http://ubuntuforums.org/showthread.php?t=83456)



In these 2 lines, where am I supposed to put the files?


sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / **putting the files in their right place**

sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / **putting the files in their right place**


Thank you

---

### Post by dyous87 on 2008-04-24
> **kelcie234 said:**
> I am trying to install the lexmark z605 by following this guide:


[http://ubuntuforums.org/showthread.php?t=83456](http://ubuntuforums.org/showthread.php?t=83456)



In these 2 lines, where am I supposed to put the files?


sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / **putting the files in their right place**

sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / **putting the files in their right place**


Thank you

it shouldn't matter, as long as you run the installation from the same directory they are extracted. To be safe just make a directory in your home folder called lexmark, and extract them to there.

/home/*user name/*lexmark

---

### Post by kelcie234 on 2008-04-24
delete

---

### Post by kelcie234 on 2008-04-24
I'm an idiot.  Nevermind. Got it.

Thanks

---

### Post by dyous87 on 2008-04-24
Nah don't worry about it. :) Glad you got it working

David

---

