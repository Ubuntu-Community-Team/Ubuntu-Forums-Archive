---
title: "Installing a modified glibc source in Ubuntu 16.04"
date: 2016-12-18
forum: New to Ubuntu
---

### Post by shehzad-khawar on 2016-12-18
Hi,
I hope all are fine.

I have a glibc source, and I am following this link ([https://www.gnu.org/software/libc/manual/html_node/Running-make-install.html#Running-make-install](https://www.gnu.org/software/libc/manual/html_node/Running-make-install.html#Running-make-install)) to install it from source. The documentation specifies 
> **[COLOR=#000000][FONT=Times]You must first build the library (‘[/FONT][/COLOR]make[COLOR=#000000][FONT=Times]’), optionally check it (‘[/FONT][/COLOR]make check[COLOR=#000000][FONT=Times]’), switch the include directories and then install (‘[/FONT][/COLOR]make install**[COLOR=#000000][FONT=Times]**’). The steps must be done in this order. **

[/FONT][/COLOR]

What does it means when it says "**[COLOR=#000000][FONT=Times] switch the include directories[/FONT][/COLOR]**"?

If anybody has some clean method to install glibc from source (any source), kindly do share it with me.

Cheers,
K

---

### Post by ajgreeny on 2016-12-18
I think you are making this more difficult for yourself than is necessary.

Assuming you have a good reason for installing from source, which is not something that many users need to do, have a read through the ubuntu-specific information at [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) rather than the more general gnu.org page you are trying to follow.

---

