---
title: "What does Hash Sum mismatch means when updating?"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lobo_tuerto on 2011-09-11
Hello guys, today when I wake up I did a: sudo apt-get update and received for the first time these messages:

> W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mx.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/mx.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


Is it normal to receive them when using a beta product? or should I worry?

---

### Post by 2F4U on 2011-09-11
In my opinion it is not normal. A hash sum mismatch means either that the calculated hash sum is wrong (the not so dramatic case) or that the package has been modified after the hash sum has been calculated (the more dramatic case, since you don't know who modified it). It may just be a lazy developer but it may also be a malicious hacker, who knows?

---

### Post by cariboo on 2011-09-11
The error message you are getting, may mean there is a problem with the mirror you are using, change to the Main server, and run an update again.

---

### Post by lobo_tuerto on 2011-09-11
Immediately running again sudo apt-get update showed not problem anymore. I was just wondering why would it show in the first place.

---

### Post by ronacc on 2011-09-11
it is possible that a bit got flipped in transit to you causing the mismatch .

---

