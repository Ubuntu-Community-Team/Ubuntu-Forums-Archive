---
title: "Help Opening File as a Binary"
date: 2008-07-23
forum: Programming Talk
---

### Post by loganwm on 2008-07-23
I'm attempting to open a file as a binary using the iostream header, can you help me?

---

### Post by era86 on 2008-07-24
I'm assuming C++.  What exactly are you having problems with?

Just do what you normally do when opening a file and create a filestream.  Use ios::binary as the mode like so:

outf.open( "filename", ios::binary );

Go here for more info:
[http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html)

---

