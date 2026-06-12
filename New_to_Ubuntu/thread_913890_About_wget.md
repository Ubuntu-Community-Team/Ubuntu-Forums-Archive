---
title: "About wget"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by satyaanveshi on 2008-09-08
I read in some posts that wget downloads file in the current directory. Can anyone tell me if there is any way to permanently configure the directory where it downloads.
Thanks

---

### Post by aloshbennett on 2008-09-08
greeting truth-seeker!
with -P (or --directory-prefix) option, you can specify the directory to which the files should be downloaded.

You could make an alias for wget as 
> alias wget="wget -P <permananet directory>"

and add it to your ~/.bashrc

---

