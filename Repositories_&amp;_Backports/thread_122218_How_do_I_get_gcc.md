---
title: "How do I get gcc"
date: 2006-01-27
forum: Repositories &amp; Backports
---

### Post by StubornAH on 2006-01-27
I ran the Synaptic Program Manager and installed the gcc package.  Then I restarted and I can't just type "gcc --version" at the command prompt.  I also tried running ./configure on a xemacs folder and it said that it could not find gcc.

So, what do I need to do to get it installed and running?


Thanks.

---

### Post by amohanty on 2006-01-27
Try:

> sudo apt-get install gcc

that should create /usr/bin/gcc file.

HTH
AM

---

### Post by StubornAH on 2006-01-27
thnx, got it now.

---

### Post by stuporglue on 2006-01-27
Odds are good that you're going to want more than just gcc though. For the rest of the usefull build tools (make, g++ others?) install build-essential.

---

