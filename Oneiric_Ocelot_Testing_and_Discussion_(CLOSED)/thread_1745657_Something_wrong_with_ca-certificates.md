---
title: "Something wrong with ca-certificates"
date: 2011-05-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-01
Hmm, the package ca-certificates cannot be upgraded into the version 20110421.
Synaptic throws an error of broken packages.

---

### Post by Yofel on 2011-05-01
Indeed, seems like ca-certificates was synced from unstable without syncing newer openssl too.

---

### Post by Harry33 on 2011-05-03
The upgraded openssl (1.0.0) solved the dependency issue.

---

