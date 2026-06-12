---
title: "Help compiling Firefox with SVG support"
date: 2005-04-26
forum: Packaging and Compiling Programs
---

### Post by JDay on 2005-04-26
I am attempting to compile Firefox with SVG support enabled. I got the sources and dependencies through apt and I have libart and cairo dev installed. I put --enable-svg in debian/rules, but the compile fails with an error like "no svg renderer". I've also tried adding --enable-svg-renderer=(libart or cairo), which didn't make any difference. Any ideas?

---

### Post by zeroK on 2005-04-29
[QUOTE=JDay]I am attempting to compile Firefox with SVG support enabled. I got the sources and dependencies through apt and I have libart and cairo dev installed. I put --enable-svg in debian/rules, but the compile fails with an error like "no svg renderer". I've also tried adding --enable-svg-renderer=(libart or cairo), which didn't make any difference. Any ideas?[/QUOTE]
 Just an idea, but does Firefox perhaps need an external libart library? Then you perhaps don't have the necessary *-dev packages installed :-)

---

### Post by JDay on 2005-04-29
[QUOTE=zeroK]Just an idea, but does Firefox perhaps need an external libart library? Then you perhaps don't have the necessary *-dev packages installed :-)[/QUOTE]
Well, I've got libart-dev libart-2.0-dev and libcairo1-dev installed. Is there anything else I need?

---

### Post by mveers on 2005-05-14
You can try with:
--enable-svg-renderer-libart
or
--enable-svg-renderer-cairo

---

