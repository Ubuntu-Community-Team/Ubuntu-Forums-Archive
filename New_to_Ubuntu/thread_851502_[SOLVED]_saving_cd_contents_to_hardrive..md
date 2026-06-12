---
title: "[SOLVED] saving cd contents to hardrive."
date: 2008-07-06
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-06
from the file browser window, how do I copy whats on this disk to my hardrive?  Or why isn't it obvious?

---

### Post by neurostu on 2008-07-06
Well you can open a 2nd window, and drag and drop all the contents to the location where you would like them to be....

or you can use the terminal, cd to the cdrom dir:
```

cd /media/cdrom
cp -r . /home/<username/<destinationDir>

```

that will do the trick.

---

### Post by lamego on 2008-07-06
Select the contents, copy, browse to your home dir, create and folder and paste, it is pretty obvious.
Anyway the recommended way to backup a CD is creating an ISO image of it, the copy/past using the file manager may not be a reliable copy depending on the CD contents.

---

### Post by adamogardner on 2008-07-06
how do I select the contents?

---

### Post by neurostu on 2008-07-07
Click and drag a box that will highlight everything... same as in windows.

---

### Post by hyper_ch on 2008-07-07
I'd also vote to make an .iso out of the cd and then mount it ;)

---

### Post by stp71 on 2008-07-07
If I'm not mistaken you can single click on any file in the window and press **[COLOR="deepskyblue"]Ctrl[/COLOR]** + **[COLOR="deepskyblue"]a[/COLOR]** to select all the content.  Then, press **[COLOR="deepskyblue"]Ctrl[/COLOR]** + **[COLOR="DeepSkyBlue"]c[/COLOR]** to copy.  

My question is, how do you get hidden files to be displayed?  I know in a term, you can just type **[COLOR="DeepSkyBlue"]ls -a[/COLOR]** to display hidden files.

---

### Post by adamogardner on 2008-07-07
ok  thankyou.

---

### Post by philinux on 2008-07-07
ctrl h

---

