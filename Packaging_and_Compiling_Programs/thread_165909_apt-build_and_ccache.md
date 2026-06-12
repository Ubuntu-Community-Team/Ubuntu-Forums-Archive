---
title: "apt-build and ccache"
date: 2006-04-25
forum: Packaging and Compiling Programs
---

### Post by timothyparker@gmail.com on 2006-04-25
I'm interested in utilizing ccache in conjunction with apt-build. I've added "/usr/lib/ccache" to my path, but is that sufficient? Will I need to add the compiler references to make options of apt-build also?
Thanks for any assistance/wisdom on this.
TDP

---

### Post by MichaelZ on 2006-04-29
Hello,

I would suggest as first thing to do a:

> 
man ccache
 

These links could also be useful:

[http://ccache.samba.org/]("http://ccache.samba.org/")
[http://www.unixreview.com/documents/s=8989/ur0402j/]("http://www.unixreview.com/documents/s=8989/ur0402j/")

Best wishes,
Michael

---

