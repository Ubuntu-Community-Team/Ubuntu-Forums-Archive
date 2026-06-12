---
title: "Create custom keywords KDevelop"
date: 2007-01-17
forum: Programming Talk
---

### Post by tomane on 2007-01-17
Hi,
I am working with kdevelop (programming in C)and so far I'm quite happy with it.
However I bumped into a small issue here; I'm creating a header typedef'ing costum data types that I plan to use in th whole project. 
How can I tell kdevelop to highlight these new keywords? It could be either considering them as if they were a base data type or by creating a class of their own.
So, can this be done? :-k

Cheers,
--to

---

### Post by Steveire on 2007-01-17
I don't have KDevelop at the moment to test it, and haven't tried this with kate either, but you could edit the file /usr/share/apps/katepart/syntax/c.xml to add the keyword you want, or copy it to your home folder and edit it there. Then edit ~/.kde/share/config/katesyntaxhighlighting.rc to point at your copy. Let me know if that works.

---

### Post by tomane on 2007-01-17
> **Steveire said:**
> I don't have KDevelop at the moment to test it, and haven't tried this with kate either, but you could edit the file /usr/share/apps/katepart/syntax/c.xml to add the keyword you want, or copy it to your home folder and edit it there. Then edit ~/.kde/share/config/katesyntaxhighlighting.rc to point at your copy. Let me know if that works.

Thanks, I edited the c.xml file in place and it worked!

Cheers,
--to.

---

