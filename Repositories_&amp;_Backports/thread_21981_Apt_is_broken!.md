---
title: "Apt is broken!"
date: 2005-03-25
forum: Repositories &amp; Backports
---

### Post by CowPie on 2005-03-25
"
dpkg: parse error, in file `/var/lib/dpkg/status' near line 1668 package `openoffice.org-bin':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
"

This is the only message I get whenever apt gets aorund to installing things, evne though it downloads finely.  What does it mean, how do I fix it?

---

### Post by ubuntu-geek on 2005-03-25
It appears the status file maybe be corrupted around like 1668.. go look in /var/lib/dpkg and see if you have a status-old file if so copy it over status and try.

There is also some helpful information here for recovering your status file.
[http://www.linuxmafia.com/faq/Debian/package-database-rebuild.html](http://www.linuxmafia.com/faq/Debian/package-database-rebuild.html)

---

### Post by cdhotfire on 2005-03-25
try to remove and install once again openoffice.org-bin

if this doesnt work. do
```
sudo dpkg-reconfigure openoffice.org-bin
```

---

### Post by CowPie on 2005-03-25
[QUOTE=cdhotfire]try to remove and install once again openoffice.org-bin

if this doesnt work. do
```
sudo dpkg-reconfigure openoffice.org-bin
```[/QUOTE]
 Should I do apt-get remove --purge or just apt-get remove?

Ubuntu-geek, I will try that in case of failure, as it looks more involved.  Thank you both for responding!

---

### Post by CowPie on 2005-03-25
[QUOTE=CowPie]Should I do apt-get remove --purge or just apt-get remove?

Ubuntu-geek, I will try that in case of failure, as it looks more involved.  Thank you both for responding![/QUOTE]
 OK, I just tried post #3.  THat openoffice.org-bin file isn't instaled, strangely!  So I tried post #2 and it did work.  Thanks again.

apt-get -f install is what apt told me to do, and we'll see how it goes..

---

### Post by az on 2005-03-25
sudo dpkg --clear-avail

That may have worked for you, too.

---

