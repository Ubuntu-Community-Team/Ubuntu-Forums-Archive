---
title: "[SOLVED] libdvdread3 help"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-06-15
I'm trying to take all the neccessary steps to be able to play DVD's, but when running the following code, I get a 404 error.

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Anybody know what's up?

---

### Post by the_doc on 2008-06-15
I think you need to install these first:

sudo apt-get install build-essential debhelper fakeroot

---

### Post by billgoldberg on 2008-06-15
Installing dvd support:

install  ubuntu-restricted-extras

Then add the medibuntu repo and install libdvdcss2

(media link in signature)

or install vlc from that same repository.

That's it.

---

### Post by subaruwrc01 on 2008-06-15
I already have those installed.  They are irrelevant to my problem.

The problem is that the file no longer is located on the host server and returns a 404 error.

---

### Post by subaruwrc01 on 2008-06-15
> **billgoldberg said:**
> Installing dvd support:

install  ubuntu-restricted-extras

Then add the medibuntu repo and install libdvdcss2

(media link in signature)

or install vlc from that same repository.

That's it.

libdvdcss is what I'm trying to get, but I'm getting a 404 error.

---

### Post by the_doc on 2008-06-15
[B]Sorry 
This site is down for maintenance until 2008-June-18[/B]

I guess that could be your problem then.

---

### Post by subaruwrc01 on 2008-06-15
Ok, I found the problem.  The server is down for maintenance.

---

### Post by billgoldberg on 2008-06-15
can't you just download vlc from vlc's website?

---

### Post by cariboo on 2008-06-15
You can install libdvdcss from the Medibuntu repositories. That way you don't have to wait for the server to come back up again.

Jim

---

### Post by amgarlin on 2008-06-16
Hey thanks the_doc at least I know know when the site will be back up. I have been wondering how long it was gonna be.

---

