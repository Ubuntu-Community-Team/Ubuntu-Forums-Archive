---
title: "How to make my self Owner and get out of Owner."
date: 2011-11-20
forum: New to Ubuntu
---

### Post by RaptorJay on 2011-11-20
I recently changed my Ubuntu 11.10 to 10.04 and I am now trying to install ubuntulooks engine but when I try to put the files needed into the usr/lib/2.0/2.10.0/engines it says I am not Owner. How can I change this and then revert it back..?

---

### Post by mike555 on 2011-11-20
in terminal type;  gksudo nautilus   .

---

### Post by nothingspecial on 2011-11-20
> **mike555 said:**
> in terminal type;  gksudo nautilus   .

That's right. System folders/files are owned by root. Rather than changing ownership to your user then back to root, you give yourself root powers by using gksudo or sudo.

:)

---

### Post by RaptorJay on 2011-11-20
Thank you it worked!!!! >.<:P

---

