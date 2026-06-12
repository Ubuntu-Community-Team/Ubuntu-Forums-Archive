---
title: "Minix vs Linux for Learning Operating System Design?"
date: 2012-01-04
forum: Programming Talk
---

### Post by haziz on 2012-01-04
I wish to learn operating system design. I was wondering if I should tackle Minix or Linux in the process? I like books so I would be following mainly a book, though video resources (presumably videotaped lectures) would also be welcome.

I have formally studied C and C# and can program small to medium sized programs in them. I also have a basic understanding of data structures.

If I take the Minix route, should I tackle version 2 (simpler??) or version 3?

I find it motivating to formally enroll in a college or University course. Any online or distance courses that cover operating system design available?

Thanks.

---

### Post by 2F4U on 2012-01-04
Minix is a more academic system, designed by a university professor. So you probably get a clean design. However, Linux is what is used in the reality (I don't know of any productive server running under Minix) and you will probably get a lot more documentation and books on Linux than on Minix.

---

### Post by whatthefunk on 2012-01-04
Linux would be a lot more practical.

---

### Post by Lars Noodén on 2012-01-04
Agreed, Linux would be much more practical.  

If you want to start smaller, OpenBSD emphasizes standards, correct design, proactive security, cryptography and good documentation.  It's almost ideal for teaching or learning since it one main channel of distribution is via source code and updates are distributed as patches.

---

### Post by haziz on 2012-01-04
> **Lars Noodén said:**
> Agreed, Linux would be much more practical.  

If you want to start smaller, OpenBSD emphasizes standards, correct design, proactive security, cryptography and good documentation.  It's almost ideal for teaching or learning since it one main channel of distribution is via source code and updates are distributed as patches.

What textbook would you recommend for studying the BSD Kernel? I am aware of Marshall Kirk McKusick's BSD and FreeBSD books (the Kernel should be mostly the same). I could also pick up Bach's book on Unix (based I believe on AT&T's System V from the eighties). Tanenbaum's Minix book may be written at a more understandable level and has a good reputation as a good OS textbook in Universities (and is after all the immediate inspiration for the Linux Kernel). Bach's book, I know less of but it also has a very good reputation. Not sure how I would get hold of 1980s era System V source code to look at the source code if I want, though I suspect that is not totally necessary.

---

### Post by Lars Noodén on 2012-01-05
The one I would recommend would be [Modern Operating Systems](http://www.amazon.com/Modern-Operating-Systems-Andrew-Tanenbaum/dp/0136006639) by Tanenbaum.  You could search around at the high tech universities and see what else they have on the relevant course syllabi. 

For the FreeBSD there is a book [Designing BSD Rootkits](http://nostarch.com/rootkits.htm).  The OpenBSD kernel is quite different from the FreeBSD kernel, it was originally forked from the NetBSD kernel.  For OpenBSD, I'd say to go with the online documentation and what's written in the code.  That project makes great effort to maintain high quality, up to date documentation.  It's a source of pride for them.  That includes comments inside the code.  It's an operating system that's designed to be built from source.

---

### Post by imagecko on 2012-01-05
Isn't Minix built from the beginning to be a OS to learn from?
I have read the book about it and think it is really good.

---

### Post by 2F4U on 2012-01-05
Minix has been created for educational purposes but it was not free from the beginning. If it would have been free as Linux, it may have gotten more attention and maybe Linux wouldn't exist. It was later re-licensed under a BSD license.

---

### Post by slavik on 2012-01-05
Use minix, it is much smaller (I think it's like 10mb) and much simpler than Linux.

---

