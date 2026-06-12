---
title: "Display"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by mihangel on 2008-10-05
I am new to Ubuntu. I have recently set up Ubuntu 8.04.1 for a dual set up with my Windows XP. Everything seems to be in order until I open a document. I have no cursor within the document and when I try to move the window it disintegrates (incomplete display element clearing?). I have been told by a non-Ubuntu user that it may be  because my HP w2207 monitor driver is incompatible with Ubuntu? Can anyone advise what might be happening?

I tried Sudoku in the Games and it functions well unless I try to move or enlarge the window.

Mihangel

---

### Post by bobnutfield on 2008-10-05
That is a graphics card issue and not your monitor.  What graphics card do you have?

---

### Post by BDNiner on 2008-10-05
You could also have desktop effects enabled and not configured properly. Try disabling the desktop effects and see if you still have problems.

---

### Post by mihangel on 2008-10-06
> **bobnutfield said:**
> That is a graphics card issue and not your monitor.  What graphics card do you have?

Bob:

Many thanks for your advice. I have AGP. I contacted HP yesterday and they confirm that it should be compatible with Linux. I am now investigating the Ubuntu driver and will investigate the desktop effects as advised yesterday.

I'm originally from the UK so it was good to get the first response from the old country!

---

### Post by bobnutfield on 2008-10-06
If you will tell us WHICH AGP card you have we can advise on the driver.  It may be that the refresh rate is wrong in Xorg.conf file, or you have the wrong graphics driver.  Open a terminal and type:

> lspci | grep VGA

That will tell you what graphics card you have.

> 
I'm originally from the UK so it was good to get the first response from the old country!

BTW, ironic, I am American, living in the UK.

---

