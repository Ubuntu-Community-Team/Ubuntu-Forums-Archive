---
title: "[SOLVED] Help with Eclipse's Visual Editor"
date: 2008-03-10
forum: Programming Talk
---

### Post by Saponsky09 on 2008-03-10
Well. after sniffing easy eclipse's documentation, I found what I need to install Visual Editor correctly...
(This is for Eclipse 3.2)

1-   download the EMF build : [here.]("http://www.eclipse.org/downloads/download.php?file=/modeling/emf/emf/downloads/drops/2.2.0/R200606271057/emf-sdo-runtime-2.2.0.zip")
2-  download the GEF build: [here.]("http://www.eclipse.org/downloads/download.php?file=/tools/gef/downloads/drops/R-3.2-200606270816/GEF-runtime-3.2.zip")
3- download VE: [VE_SDK]("http://www.eclipse.org/downloads/download.php?file=/tools/ve/downloads/drops/R-1.2.3_jem-200701301117/VE-SDK-1.2.3_jem.zip")
4- Then extract all the files to your .eclipse directory. The directory can be found by hitting 'ctrl + h' in your home directory and then search for the .eclipse dir.
***Caution specify a different dir name than eclipse for your extracted dir***
5- go to the extracted dirs, make a subdir and name it eclipse and add a file named .eclipseextension then add all the files to the eclipse subdir.
6- Then open eclipse, go to help -> manage configuration.  Go to specify an extension (or something, sorry can't remember the option right now, I'm not at home, I'll update the thread later :D)
select there your eclipse subdirs.
7- restart eclipse.

PS: I think there is not enough documentation for this project, I mean I had to go through a lot just find how out to install this extension.

*I need help, installing Eclipse's Visual Editor to run Visual classes and GUIs.  I followed the site's installation how-to FAQ but it does not seems to work. I also downloaded the .ZIP package and added to my eclipse dir but nothing.  Have anyone installed it on ubuntu? Tanx for you attention.*

---

### Post by Saponsky09 on 2008-03-10
*bump*

---

### Post by mrfuzzemz on 2008-04-28
> **Saponsky09 said:**
> 6- Then open eclipse, go to help -> manage configuration. Go to specify an extension

You can have it automatically install by finding updates and new features from this menu.

---

### Post by h_hosseinioun on 2008-09-13
Thnx man. u really helped me

---

