---
title: "[SOLVED] Ubuntu to silently cache more?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by skymera on 2008-09-13
Hello

Is there a way for Ubuntu to silently cache programs whilst at desktop?

I've used Preload ans saw no difference. In "top" i have 1.9GB free RAM which is effectively wasted RAM.

So i just want to put it to use really.

---

### Post by Vadi on 2008-09-13
Used != cached. Cached is shown separately.

Try using the system monitor to see how much is cached. Usually ubuntu nearly maxes out the memory for caching, by default.

---

### Post by skymera on 2008-09-13
top - 13:58:51 up  2:01,  2 users,  load average: 1.14, 0.91, 0.52
Tasks: 106 total,   2 running, 104 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.8%us,  0.1%sy,  0.0%ni, 76.0%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3095584k total,  2632504k used,   463080k free,   316768k buffers
Swap:  1951888k total,        0k used,  1951888k free,  1374472k cached

It's more but 463MB free

---

### Post by Vadi on 2008-09-13
No actually only 146MB (3095584 &#8722; 2632504 &#8722; 316768 = 146312), which is a fine amount to leave.

---

### Post by skymera on 2008-09-13
I realised that, my mistake :P

Misread

---

