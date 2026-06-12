---
title: "Connecting to sqlite or mysql"
date: 2008-05-31
forum: Programming Talk
---

### Post by brettnak on 2008-05-31
Is there a mysql or sqlite service running on ubuntu by default?

---

### Post by Majorix on 2008-05-31
As far as I know, there is no database software installed on Ubuntu. However doing a search in your Synaptic would reveal the packages you can install.

---

### Post by LaRoza on 2008-05-31
> **brettnak said:**
> Is there a mysql or sqlite service running on ubuntu by default?

sqlite isn't a service, it is a C library.

MySQL isn't installed on the desktop version by default.

SQLite is used by many apps, including Firefox.

---

### Post by pmasiar on 2008-05-31
> **LaRoza said:**
> sqlite isn't a service, it is a C library.

It means SQLite does not have server running, administration (and does not allow multiple users). This is why SQLite is excellent choice for embedded databases, and for SQL development: database is just a file with special structure, you can copy it, make backup, run another SQL query against it, etc.

---

### Post by LaRoza on 2008-05-31
> **pmasiar said:**
> It means SQLite does not have server running, administration (and does not allow multiple users). This is why SQLite is excellent choice for embedded databases, and for SQL development: database is just a file with special structure, you can copy it, make backup, run another SQL query against it, etc.

Yes, it is a very handy library especially the way it is so easy to use.

---

