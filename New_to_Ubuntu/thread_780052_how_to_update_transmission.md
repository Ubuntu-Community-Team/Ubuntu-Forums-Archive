---
title: "how to update transmission?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by lazydesi on 2008-05-03
Hi folks,

I got transmission 1.06 version, how can i update to 1.11 (which is current version) in hardy 8.04?

---

### Post by Moop on 2008-05-03
getdeb.net has the newer version. [http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

---

### Post by lazydesi on 2008-05-03
thanks Moop

---

### Post by lazydesi on 2008-05-03
Moop,

It's comming up with " the dependency is not satisfiable":confused::confused::confused:

---

### Post by zaussome on 2008-05-03
z

---

### Post by Paqman on 2008-05-03
> **lazydesi said:**
> Moop,

It's comming up with " the dependency is not satisfiable":confused::confused::confused:

Have you got Universe/Multiverse/Proposed enabled?

---

### Post by lazydesi on 2008-05-03
> **Paqman said:**
> Have you got Universe/Multiverse/Proposed enabled?
yep it's enabled

---

### Post by Moop on 2008-05-03
There are two files that need to be installed in the right order. I think the transmission-common should be first then the transmission-gtk.

edit: It looks like you need to remove transmission-gtk first and then install the two debs in the order I suggested.

---

### Post by lazydesi on 2008-05-03
> **Moop said:**
> There are two files that need to be installed in the right order. I think the transmission-common should be first then the transmission-gtk.

edit: It looks like you need to remove transmission-gtk first and then install the two debs in the order I suggested.

yepp got it

first common then second one.

now it's working:guitar::guitar::guitar:

thanks mate

---

