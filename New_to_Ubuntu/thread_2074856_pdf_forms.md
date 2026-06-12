---
title: "pdf forms"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2012-10-22
I am wondering besides Acroread (which is slow and bloated and god knows when will Adobe kill it for Linux) is there an open source pdf reader that can fill forms properly. I have tried evince and Okular and both have problems handling even very common forms (sometimes cannot save, sometimes text fields are missing, and scripts don't work say for tax forms which will automatically produce the sum when enter the separate items) 

At this point my solution is to run pdf Xchange viewer in Wine which is fast and light and works perfectly.  But I would rather not to use Wine.

There are many open source viewers, but it seems that all of them just basically do the same thing and more or less equally defective in that they lack some very basic and essential features. Okular is weird and not always works(text fields missing or not even recognises a form), LibreOffice draw is not really a pdf viewer and as far as I know doesn't work with scripts like the one I described about tax forms. inkscape can produce forms that support scripts but apparently cannot fill them (??) and it seems overkill especially for the common user.

Sadly when I install Ubuntu for others I have to make PDF Xchange viewer the default pdf reader just in case they may need to fill forms.

Any suggestion or if not, an explanation why pdf is such a problem for Linux? Thanks.

---

### Post by HermanAB on 2012-10-22
I use xournal and pdfshuffler to do whatever I want with PDFs.

---

### Post by monkeybrain2012 on 2012-10-22
> **HermanAB said:**
> I use xournal and pdfshuffler to do whatever I want with PDFs.

I don't think you can fill a tax form with xournal if it has scripts on it. pdfshuffler is just for rearranging and combining pdf files if I am not mistaken (I use pdfchain for those purposes)

---

### Post by Peripheral Visionary on 2012-10-22
Xournal is a pdf **annotator** - perfect for filling out those forms. It's also a cool note-taking app for school.

---

### Post by monkeybrain2012 on 2012-10-29
Found two new ways to do this. 

First there is this [http://www.cabaret-solutions.com/](http://www.cabaret-solutions.com/) It runs natively in Linux and it seems that even the free (as beer) version has some nice features (there is an English version you can download and it doesn't require installing, just untar the archive, go to /bin and run the script)

There is also an online pdf editor (if you feel safe to fill your forms  and edit your pdf files this way)

[http://www.pdfescape.com/](http://www.pdfescape.com/)


EDITED: Forgot to mention pdfedit, but it seems very chaotic and counter-intuitive and the manual is very complex and confusing,  it seems not worth the troubles if I just want to fill a form and print it.

---

### Post by Peripheral Visionary on 2012-10-29
For just filling out forms, Xournal is perfect, pretty, and simple.  Best of all it's already in the Ubuntu repositories and installs in seconds.

---

### Post by monkeybrain2012 on 2012-10-29
> **Peripheral Visionary said:**
> For just filling out forms, Xournal is perfect, pretty, and simple.  Best of all it's already in the Ubuntu repositories and installs in seconds.

I may be missing something but it doesn't seem to support forms with scripts. For example, you enter a bunch of numbers on a tax form and it produces the total. If it is just a plain form without script I think Okular and evince can do it too.(Evince cannot save many forms for re-editing, but if the form has no script and you can fill it in one go then you can always print it instead of saving it)

---

