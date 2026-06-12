---
title: "monodevelop 4 in ubuntu 14.04 closed unexpectedly when try to svn checkout or open ol"
date: 2014-04-30
forum: Programming Talk
---

### Post by jambel on 2014-04-30
I installed Ubuntu 14.04 in couple of computers and I experience the same problem in both of them.
  
When I go to version control menu to checkout a project even when I  try to open an older version solution (ubuntu 12.04 - mono 3.1.0? I  think) mono closed unexpectedly without any warning message.

If I try to create a new solution it works ok.

Any ideas?
Thanks.

---

### Post by jambel on 2014-04-30
monodevelop version 4.0.12
Problem type: Crash
Title: MonoDevelop.exe crashed with SIGABRT in svn_stringbuf_ensure()

---

### Post by jambel on 2014-05-02
Done, upgrade to 4.2.2 from source and problem solved!

---

