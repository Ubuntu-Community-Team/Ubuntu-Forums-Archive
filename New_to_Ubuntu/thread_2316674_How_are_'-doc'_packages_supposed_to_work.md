---
title: "How are '-doc' packages supposed to work?"
date: 2016-03-09
forum: New to Ubuntu
---

### Post by RadonPlasma on 2016-03-09
I mostly got into GNU/Linux as a more development-focused system. To that end, I try to have local copies of the documentation for the libraries I want to work with. The problem is, there is almost no information about where the documents end up after the packages are installed. After quite a bit of digging, I learned about doc-base, which is a step in the right direction. After that I tried installing doccentral, but that was completely non-functional. Here Ubuntu comes installed with a help viewer, but it doesn't seem to be usable with anything but the basic 'How to Use Ubuntu' pages. Is there a recommended application, or is hunting through /usr/share/doc/ the typical solution?

---

### Post by sandyd on 2016-03-09
There is no reader for /usr/share/doc that works like the man command. It is mainly because content varies accross all the doc folders. Some use gzip to compress their documents/changelog, some use html, etc etc.

Most of the packages there use either gzip or html, so you the general method for reading seems to be simply opening whatever is in the doc folder for the app.

Hope that helps!

---

### Post by RadonPlasma on 2016-03-10
Hm. dwww tries to do what doc-central was supposed to do, but fails to generate links properly. Oh, well. Thanks for your help.

---

### Post by bab1 on 2016-03-10
> **RadonPlasma said:**
> I mostly got into GNU/Linux as a more development-focused system. To that end, I try to have local copies of the documentation for the libraries I want to work with. The problem is, there is almost no information about where the documents end up after the packages are installed. After quite a bit of digging, I learned about doc-base, which is a step in the right direction. After that I tried installing doccentral, but that was completely non-functional. Here Ubuntu comes installed with a help viewer, but it doesn't seem to be usable with anything but the basic 'How to Use Ubuntu' pages. Is there a recommended application, or is hunting through /usr/share/doc/ the typical solution?
Read the manual page for *man*```
man man
```  **Man** is a pager (reader) that extracts and formats the documentation in a specific manner.  You should not read the information directly from /usr/share/doc.  You can invoke the command **man** from anywhere in the file system at the command line (terminal).  The basic syntax is: man <term>.

If you prefer the Ubuntu man pages in HTML, you will find them [**here**]("http://manpages.ubuntu.com/")

---

### Post by oldos2er on 2016-03-10
> **RadonPlasma said:**
> I mostly got into GNU/Linux as a more development-focused system. To that end, I try to have local copies of the documentation for the libraries I want to work with. The problem is, there is almost no information about where the documents end up after the packages are installed. 

```
dpkg -L <package name>
``` will work.

> **RadonPlasma said:**
> After quite a bit of digging, I learned about doc-base, which is a step in the right direction. After that I tried installing doccentral, but that was completely non-functional. Here Ubuntu comes installed with a help viewer, but it doesn't seem to be usable with anything but the basic 'How to Use Ubuntu' pages. Is there a recommended application, or is hunting through /usr/share/doc/ the typical solution?

You can view gzipped files without unzipping them using *less*, e.g. ```
less README.gz
``` But as bab1 points out *man command* is more convenient.

---

