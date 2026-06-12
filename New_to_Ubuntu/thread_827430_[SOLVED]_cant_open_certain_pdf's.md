---
title: "[SOLVED] cant open certain pdf's"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by concerto on 2008-06-12
Where can I change my pdf options?  I have been getting the following error message....



/tmp/Camp_Perry_Web.pdf could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location.




Any advice would be awesome.  Thank you.

---

### Post by gr4nf on 2008-06-12
Thats a permissions problem. Try saving to your home directory, where you know you have write access.

---

### Post by drs305 on 2008-06-12
Which pdf viewer are you using - evince, acrobat or something else? It only matters in how you may be able to set the default save location, if that is possible.

It appears you are trying to save the file to /tmp which is owned by root. You should change the save location to somewhere within your own home folder and then should be able to save a copy of the pdf file.


ah - what gr4nf said.... sidetracked during the writing ...

---

### Post by concerto on 2008-06-12
Looks like I'm using the standard doc viewer that came with Ubuntu, I think it's called "EVINCE".   I figured out how to open the document now but the screen turns black when trying to open in.  I'll keep working on it.  I will try a new reader.  Thank you everyone.

---

### Post by kansasnoob on 2008-06-12
I'd think you'll want to add the Medibuntu repository:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then go to synaptic and install acroread (which is adobe).

---

### Post by kaibob on 2008-06-12
> **concerto said:**
> ...I will try a new reader.  Thank you everyone.

You might want to try the display utility from the Imagemagick package. If it won't open the PDF, it should give an error message that will help with troubleshooting. Open a terminal window, change to the directory that contains the PDF, and type:

```
display pdffilename
```

BTW, Imagemagick is not installed by default, but it's small in size and very, very useful.

---

