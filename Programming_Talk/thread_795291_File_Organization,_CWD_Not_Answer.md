---
title: "File Organization, CWD Not Answer"
date: 2008-05-15
forum: Programming Talk
---

### Post by JupiterV2 on 2008-05-15
Q1. Where, in Linux/Unix, should files be placed that are to be loaded at runtime? Like dictionaries, images, etc.?

Q2. How can GNU auto* be taken advantage of to place these files in the appropriate location and then provide a #define into config.h so a macro definition can be inserted into the code?

I can't seem to find any info on this anywhere...even a link would be nice.

---

### Post by JupiterV2 on 2008-05-16
Bump

---

### Post by dwhitney67 on 2008-05-16
Read this wiki on the [Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") -- hopefully this will assist you with an answer to your question.

P.S.  Consider /opt for application, and /etc/opt for config files, etc.

---

