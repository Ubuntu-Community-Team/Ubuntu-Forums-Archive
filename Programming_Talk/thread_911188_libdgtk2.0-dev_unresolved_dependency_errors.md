---
title: "libdgtk2.0-dev unresolved dependency errors"
date: 2008-09-05
forum: Programming Talk
---

### Post by henryrhenryr on 2008-09-05
I'm trying to have a go at making my own GTK apps.  To compile the C code I think I need to have libgtk2.0-dev but synaptic gives me a long list of dependencies.  Then an error:

libgtk2.0-dev: 
Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
Depends: libcairo2-dev but it is not going to be installed
Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
Depends: libgtk2.0-0 (= 2.12.9-3ubuntu2) but 2.12.9-3ubuntu4 is to be installed
Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed


I found a few references to the error which are 2 years old and refer to Dapper.  Can anyone tell me what I'm doing wrong?  I have tried updating and reloading the repositories.  The installation is about 2 months old.

Thanks!

Henry

---

### Post by henryrhenryr on 2008-09-05
Sorry.  Found the solution - I didn't update everything - only the security updates.  I added the 'recommended' updates, ran the update and now the packages install correctly.

---

