---
title: "where do i can find my kernel-headers for amd64??"
date: 2006-02-28
forum: Programming Talk
---

### Post by flapane on 2006-02-28
i compiled my 2.6.15-2 kernel, but now I need the kernel headers for compiling the fglrx module....
i can't find them nowhere!!!!!!
please someone could help me..
everyone say: you've just download your headers...
yes, but, where........

---

### Post by K.Mandla on 2006-02-28
I thought they went into /usr/src, but I'm probably wrong. No doubt you looked there already.

---

### Post by flapane on 2006-02-28
yep, no dubt;)

---

### Post by hod139 on 2006-02-28
The headers will be wherever you extracted the source, or am I not understanding something?

Or if you really want, you can install the linux-headers-2.6.15-2-* package, which will put the headers at /usr/src/linux-headers-*, but that would be a waste of disk space.

---

### Post by flapane on 2006-02-28
why a waste? headers aren't smaller than source(50mb)?
Anyway I can't find any repos where to find my headers..
any suggests?

---

### Post by flapane on 2006-02-28
ne1 could give me good repos for headers 2.6.15-2?

---

### Post by hod139 on 2006-02-28
I'm not sure where you you got your source pakage from.  The only ubuntu package is [linux-headers-2.6.15-14]("http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-14") available in Dapper.

---

### Post by flapane on 2006-02-28
i downloaded the 2.6.15-2 src from kernel.ork and compiled by myself
According to you linux-headers-2.6.15-14 could be ok even with my kernel -2 ?

---

### Post by hod139 on 2006-02-28
Too be honest, I'm not 100% sure.  I think because they are both 2.6.15 kernels, it should be compatible.  The other option is to download the ubuntu [2.6.15-16.23 kernel source]("http://packages.ubuntu.com/dapper/devel/linux-source-2.6.15"), and then reuse you .config from before to compile it.  Then you know for sure that the [ubuntu 2.6.15-16.23 headers]("http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-16-686") and source match.

---

### Post by flapane on 2006-03-01
all right thank you for info, i will try to install ati drivers with these headers, othwerwise i will recompile the newest kernel...

---

