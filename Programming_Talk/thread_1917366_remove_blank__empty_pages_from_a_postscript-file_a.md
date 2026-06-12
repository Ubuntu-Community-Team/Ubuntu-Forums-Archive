---
title: "remove blank / empty pages from a postscript-file and renumber the pages afterwards"
date: 2012-01-29
forum: Programming Talk
---

### Post by dew drop on 2012-01-29
Is there anybody out there who can help me with the following issue:

How can i remove blank or empty pages from a PostScript-file and renumber the pages afterwards? I was thinking of using awk or perl - or perhaps even PostScript-Code. 
This is an example how a blank page looks like in my PostScript-file:

```
%%Page: 4 4
%%PageOrientation: Landscape
%%PageBoundingBox: 18 18 279 402
%%BeginPageSetup
%
%%EndPageSetup
gsave
[ 0 0.24 0.24 0 18 18] concat
gsave
grestore grestore
showpage
%%PageTrailer
```

I have searched the web but couldn´t find what I was looking for. Unfortunately I have no idea how to use awk e.g. or to start.

Anybody who can help?

Thank you very much,

drew drop

---

