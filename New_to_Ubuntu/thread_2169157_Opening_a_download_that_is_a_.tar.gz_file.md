---
title: "Opening a download that is a .tar.gz file"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by ronmlinux on 2013-08-20
I downloaded OpenOffice (had some probs w/ LibreOffice) and it comes as a .tar.gz file.  How do I open and install this program?

---

### Post by papibe on 2013-08-20
Hi ronmlinux.

That is a compress file, much like a zip file. Start by right clicking on the file and select 'Extract here'

After that, I don't know. There's no standard for installing packages downloaded from the Internet. They usually will include specific instructions in one or several text files. Look for files named 'README', 'Instructions', 'Installation', etc.

Hope it helps.
Regards.

---

### Post by Kevin_Arnold on 2013-08-20
You can just click the tar.gz file and it should open up to show you what is inside (just like a zip file). If you clicked the download button on the homepage though, you have an RPM instead of a .deb file. Go here: [http://www.openoffice.org/download/other.html](http://www.openoffice.org/download/other.html) and choose the the .deb download (32 or 64 bit).

Once you have that, just open the download and then double click the .deb file. There is a PPA to install through apt-get as well but this should work for you.

---

### Post by ibjsb4 on 2013-08-20
I find OpenOffice in the software center.  Your ubuntu version does not have it there?

---

### Post by r_avital on 2013-08-20
> **ibjsb4 said:**
> I find OpenOffice in the software center.  Your ubuntu version does not have it there?

FWIW, running on 13.04, I don't see OpenOffice in the software-center.  Synaptic has a few thesaurus and hyphenation packages for non-US English and a few foreign languages.

Thanks for the link, Kevin!

---

### Post by alphacrucis2 on 2013-08-20
I guess they don't bother to maintain openoffice package in the repos once the move to libreoffice was made.

---

### Post by monkeybrain20122 on 2013-08-21
You have to remove all the LibreOffice stuffs if you want to install openoffice or you will have conflicts.

---

