---
title: "Wget question"
date: 2010-01-29
forum: Programming Talk
---

### Post by Slaktarn on 2010-01-29
Hay everyone its me again :)

If i have and just will download from that dir and don´t get redirection  to the main folder after it downloaded from that one how do i do that?

[PHP]wget -r -A "*.rar" -A "*.bin" -A "*.exe"  http://somesite:80/somedir/somedir/[/PHP]Mvh Slaktarn

---

### Post by firefly2442 on 2010-01-29
[http://www.gnu.org/software/wget/manual/html_node/Directory_002dBased-Limits.html](http://www.gnu.org/software/wget/manual/html_node/Directory_002dBased-Limits.html)

I think you may want to try "--no-parent".  I'm not 100% sure but it's worth a try.

Cheers.

---

### Post by Slaktarn on 2010-01-29
> **firefly2442 said:**
> [http://www.gnu.org/software/wget/manual/html_node/Directory_002dBased-Limits.html](http://www.gnu.org/software/wget/manual/html_node/Directory_002dBased-Limits.html)

I think you may want to try "--no-parent".  I'm not 100% sure but it's worth a try.

Cheers.


yeh that worked thx alot

/Slaktarn

---

