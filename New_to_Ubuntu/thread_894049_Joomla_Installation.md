---
title: "Joomla Installation"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by skrap on 2008-08-18
Somehow I installed the tar.gz file without extracting it.  Is there a way to back and xtract after install?  Seems to be Ok except for this.  When I point my browser to [http://localhost/joomla](http://localhost/joomla)  I get the index page but no gui.  Any help would be welcomed and appreciated.  Using gutsy on amd 64 machine.

---

### Post by cozmicharlie on 2008-08-19
You should be able to go into the folder and extract it (right click >extract here). Make sure it is in the folder you want it to extract to.

---

### Post by skrap on 2008-08-19
Thanks cozmicharlie,

I tried that.  Since the file is in root I used gksudo nautilus and the extract menu does not come up.  It is a tar.bz2 file and I installed it using the terminal following the ubuntu documentation.  I'm pretty sure that if I get this file extracted joomla will work for me.  How would I extract it using terminal?

---

### Post by Nepherte on 2008-08-19
```
tar xvfj filename.tar.bz2
```

---

