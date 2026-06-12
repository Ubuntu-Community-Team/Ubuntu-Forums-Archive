---
title: "Indexing an ftp server"
date: 2010-11-30
forum: Programming Talk
---

### Post by conradin on 2010-11-30
Hi all,
I want to index an ftp server so I can find the files I need easily. 
is there a package out there which will do this for me? Alternatively,
if I have to program something to do this, how should I go about it?

(I'm familiar, with C,C++, VB, Web coding, bash, and Expect programming)

---

### Post by Zugzwang on 2010-11-30
Hmm, what about mounting your ftp server using FUSE ([http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)) and using an ordinary indexing program for local files?

---

### Post by conradin on 2010-11-30
Its not local, its one I have access to though. 
there's a lot of files in there, only  few I need, and its not particularly well laid out.

---

### Post by Zugzwang on 2010-12-01
> **conradin said:**
> Its not local, its one I have access to though. 


Which is why I suggested using FUSE - it allows you to treat a remote ftp server like a local directory.

---

### Post by conradin on 2010-12-03
Ah much thanks, 
After trying a bogus package which gave me glib-2.0 errors, I found it in the repos and installed it. Works well, thanks again for the recommendation!

---

