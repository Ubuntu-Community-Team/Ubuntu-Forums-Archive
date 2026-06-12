---
title: "What dev'p s/w comes with Ubunto CD?"
date: 2006-10-12
forum: Programming Talk
---

### Post by tananaBrian on 2006-10-12
Hi,

  I just obtained the Ubuntu desktop CD (runs like a Live CD then click icon to intall to hard disk) :D but haven't installed it yet.  I'm interested in having a development environment (KDevelop or Eclipse) plus the Gnu C++ (gcc) compiler/linker.  I'm not, while at work and always in a hurry, finding the answer online in the FAQs and other docs ...but what comes with the standard single-CD desktop installation version of Ubuntu?  Do I need to d/l the DE/IDE and tools seperately??? :-k 

Thanks a mil!
Brian
Fairbanks, AK

---

### Post by Guido Loupias on 2006-10-12
Yes you need to download them from the repos.
From the top of my head the packages you'll probably need are...

build-essential
autotools
autoconf
automake
libtool
kdevelop (or anjuta or eclipse-cdt)

[edit]
depending on how large your RAM is you can also
try these out directly from the livecd by running
Synaptic from the livecd and installing the packages
[/edit]

---

### Post by tananaBrian on 2006-10-12
Thanks.  I'll ask the SA's at work what they install as well... feedback and/or additional info is welcome...

Brian

---

