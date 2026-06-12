---
title: "Unable to add samba shared printer in KDE"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by medley on 2008-07-20
Hi all

I'm having trouble adding a printer, shared on a Windows box, to KDE using the CUPS wizard. It's always been straightfoward when I've installed it on other systems. I just installed hardy. I also have a box running gutsy and it was trivial to do.

The error in the wizard says 'unable to create temporary printer' and no printer is added. I was able to create the printer using the CUPS web interface on port 631, but it fails when I try to print a test page. The message says it's unable to connect to the CFIS server, or something to that effect.

I am able to browse all the filesystems on my other boxes (a mixture of Linux and Windows) that are in the same Windows workgroup.

Any ideas?

---

### Post by medley on 2008-07-20
> **medley said:**
> Hi all

I'm having trouble adding a printer, shared on a Windows box, to KDE using the CUPS wizard. It's always been straightfoward when I've installed it on other systems. I just installed hardy. I also have a box running gutsy and it was trivial to do.

The error in the wizard says 'unable to create temporary printer' and no printer is added. I was able to create the printer using the CUPS web interface on port 631, but it fails when I try to print a test page. The message says it's unable to connect to the CFIS server, or something to that effect.

I am able to browse all the filesystems on my other boxes (a mixture of Linux and Windows) that are in the same Windows workgroup.

Any ideas?

Bump

---

### Post by fenian on 2008-07-20
Make sure you have all the necessary samba packages installed (I had a similiar problem on an intallation and it turned out I was missing a package though I cannot recall which one).The packages you need are....

samba samba-common smbclient smbfs

---

### Post by medley on 2008-07-21
> **fenian said:**
> Make sure you have all the necessary samba packages installed (I had a similiar problem on an intallation and it turned out I was missing a package though I cannot recall which one).The packages you need are....

samba samba-common smbclient smbfs

Thanks for the response, however all of those files are installed. Still looking for more suggestions....

---

### Post by medley on 2008-07-21
> **medley said:**
> Thanks for the response, however all of those files are installed. Still looking for more suggestions....

Bump

---

### Post by Chen Jun on 2008-12-03
I am facing same issue. It was working in 7.10.

---

