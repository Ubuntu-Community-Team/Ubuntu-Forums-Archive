---
title: "Geany issue - all text the same color, no color changes for syntax."
date: 2013-10-12
forum: Programming Talk
---

### Post by n44M4QP on 2013-10-12
Ubuntu 12.04 LTS.

In Geany .21 I'm having a weird problem where there text is always the same color, there is no auto-change for different syntax.  I've tried different color schemes, the default, etc.  Tried re-installing Geany but that didn't fix it.  Also, there's always a white vertical line in the middle of Geany which I haven't seen before.  I can't find anything on the web related to this issue.  Attached are two screenshots of a default Rails Gemfile, one using the default Geany color scheme and one using the Dark theme. 

Any ideas?  Thanks.



Default color scheme
[IMG]http://i.imgur.com/mInqFtu.png[/IMG]


"Dark" color scheme
[IMG]http://i.imgur.com/PgBEQvP.png[/IMG]

---

### Post by The Cog on 2013-10-12
Has geany been able to identify the document type? It normally uses the file name. It it's not the normal filename extension, Geany may just be treating is as a plain text file. Use the menu **Document** -> **Set filetype** to make sure geany knows how to colour it.

---

### Post by n44M4QP on 2013-10-12
That was it, sorry for the noob question!

---

### Post by The Cog on 2013-10-12
Good. Don't apologise though - it's what these forums are for.

---

