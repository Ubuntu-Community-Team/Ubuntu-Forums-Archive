---
title: "can We get source file from .deb file and How?"
date: 2009-10-13
forum: Programming Talk
---

### Post by vksingh on 2009-10-13
Hi,

How can I get source code(source file) from a .deb file.


Thanks,

Vivek

---

### Post by nvteighen on 2009-10-13
1) Activate the sources repositories.
2) In a terminal, do: apt-get source <package> without sudo (be careful... the best is to create a directory, cd into it and then do that command).

---

