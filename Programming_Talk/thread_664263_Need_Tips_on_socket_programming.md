---
title: "Need Tips on socket programming"
date: 2008-01-11
forum: Programming Talk
---

### Post by driplock on 2008-01-11
currently i am learning perl and C..any tips to boost up the process in learning socket programming...

---

### Post by wolfbone on 2008-01-11
Read the texinfo documentation - it has comprehensive descriptions and example code. Many people seen to be either completely unaware of the texinfo documentation for the GNU C library (and other things) or they do not realise that it is not just man pages in info format. 

$ info libc sockets 

In Emacs:

M-x info <RET> g(libc)sockets <RET>

---

### Post by amo-ej1 on 2008-01-11
Google for 'Linux socket tutorial'. There isn't really much difficulty in learning how sockets work. Simply read up on some manpage especially:
man socket , man bind , man accept, man listen , man tcp , man udp and man ip. Simply try to focus on a simple goal, start with  writing a simple echo client and server. 
And if anything goes wrong, strace will be your saviour ;)

---

