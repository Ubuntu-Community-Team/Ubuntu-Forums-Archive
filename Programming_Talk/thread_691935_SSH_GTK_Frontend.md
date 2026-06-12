---
title: "SSH GTK Frontend"
date: 2008-02-09
forum: Programming Talk
---

### Post by Naveen Chandran on 2008-02-09
I am trying to create a GTK frontend for ssh which includes tunneling, port forwarding feature..

no idea how to implement it any ideas...

are there any libraries?
ncind is online now Report Post   	Edit/Delete Message

---

### Post by OoooMatron on 2008-02-09
.dont know

---

### Post by fyplinux on 2008-02-09
Good idea.......

One un-flexible way is using pipes or pseudo-terminals to send the command to, and to capture the output of the ssh commands to GUI. I only heard about this method, but never did something like that.

A better way might be using some library or routines(which is also something that I am looking for) to manipulate the ssh commands. 

Any better idea? Hope someone could answer this post.

---

### Post by Smygis on 2008-02-10
[http://pyssh.sourceforge.net/](http://pyssh.sourceforge.net/) Someting like that? or [http://www.lag.net/paramiko/](http://www.lag.net/paramiko/)

---

### Post by mssever on 2008-02-10
You could check out how PuTTY works...

---

### Post by fyplinux on 2008-02-10
Finally, I found a reliable C library: [http://www.libssh2.org/wiki/index.php/Main_Page](http://www.libssh2.org/wiki/index.php/Main_Page)

---

