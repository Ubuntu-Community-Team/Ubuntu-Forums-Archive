---
title: "No manual entry for socket in section 2"
date: 2006-11-09
forum: Programming Talk
---

### Post by Ariod on 2006-11-09
Hello,

I'm having a course on network programming, and the instructions say to reference socket(2) for additional information on the socket() function arguments. However, upon calling ```
man 2 socket
``` I'm getting the error  ```
No manual entry for socket in section 2
``` How to acquire this manual entry, do I need to download some extra packages? Thanks.

---

### Post by lloyd_b on 2006-11-09
I'm not certain, but I believe that the package "manpages-dev" contains the section 2 man pages.

Lloyd B.

---

### Post by Ariod on 2006-11-09
> **lloyd_b said:**
> I'm not certain, but I believe that the package "manpages-dev" contains the section 2 man pages.

You were right, thanks!

---

