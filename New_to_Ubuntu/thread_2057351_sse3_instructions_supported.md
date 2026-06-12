---
title: "sse3 instructions supported?"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by newport_j on 2012-09-13
How can I tell if my 4 core Xeon Intel processor can support sse3 instructions?
 
Any help appreciated. Thanks in advance.
 
Newport_j

---

### Post by mcduck on 2012-09-13
running "*cat /proc/cpuinfo*" in a terminal should list SSE3 if it's supported.

Although the CPU would have to be really old one to lack SSE3 instructions, I'm not sure if there even is a quad-core Xeon that wouldn't support them...

---

