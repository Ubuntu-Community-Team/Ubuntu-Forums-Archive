---
title: "opening docx,xlsx documents"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by pkj on 2008-07-24
Hi,
Using open-office 2.2
How to open docx, xlxs files

pkj

---

### Post by kestrel1 on 2008-07-24
I have a feeling that you will have to wait until Open Office 3 is available before you can open these files in OO.
You could always use VirtualBox to run a version of Windows, Have an older version of MS Office install (2000) & install the converter from MS. Then save them to the .doc or .xls format.
I don't think that Office & the docx converter would work well under Wine.

---

### Post by Joeb454 on 2008-07-24
I've managed to open them in OO.o (I think it may've been 2.3 or 2.4 that I used though).

You just need to force it to open them :) Though you can't save it back to the same file format

---

### Post by pmlxuser on 2008-07-24
Just update your version of open office to 2.4 you can open and as said above you cannot save into the docx format. But you can open (read only) from which you can save to other formats. ;)

---

### Post by MatthiasHeil on 2008-07-24
Use [http://www.zamzar.com/](http://www.zamzar.com/) if you dislike OpenOffice.

---

### Post by WRDN on 2008-07-24
You can use any version of Open Office to open the documents, and Open Office 3 (released September 16th) will include built-in support for the formats.
Currently, you can use the [odf-converter-integrator]("http://katana.oooninja.com/w/odf-converter-integrator") with Open Office to open Office 2007 documents. This is available in the repositories.

---

### Post by Seisen on 2008-07-24
> **pkj said:**
> Hi,
Using open-office 2.2
How to open docx, xlxs files

pkj

Since you have openoffice 2.2 you will need to install the odf-converter WRDN mention. Now in openoffice 2.4 you can open those files without any problems.

---

### Post by pkj on 2008-07-24
while trying to install odf-converter-integrator, i am getting the following error

dpkg: error processing odf-converter-integrator-chocolate*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 odf-converter-integrator-chocolate*deb

pkj

---

### Post by WRDN on 2008-07-24
> **pkj said:**
> while trying to install odf-converter-integrator, i am getting the following error

dpkg: error processing odf-converter-integrator-chocolate*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 odf-converter-integrator-chocolate*deb

pkj

Did you download the package from the provided link, or are you downloading from Synaptic Package Manager (recommended)?

---

### Post by Joeb454 on 2008-07-24
What command are you running?

You can also double click the .deb file to install it :)

---

### Post by pkj on 2008-07-24
tried to download from the link
pkj

---

### Post by pkj on 2008-07-24
tried with .deb file
installation seems to have completed.

while accessing a .xlsx file as a mail attachment, i do not know how to open this file..

pkj

---

### Post by kestrel1 on 2008-07-24
How about upgrading OO to 2.4.1? I haven't needed to open any docx files, but the others are saying it works, why not try it.

---

### Post by WRDN on 2008-07-24
> **pkj said:**
> tried with .deb file
installation seems to have completed.

while accessing a .xlsx file as a mail attachment, i do not know how to open this file..

pkj

It should be possible to just open the file in the Open Office Spreadsheet program, and the converter will then convert the file before opening it in the Oo Program. There is no need to manually convert the file.

---

