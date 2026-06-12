---
title: "compiling a module"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by rezaf on 2012-12-30
Hi, I have source files of a driver module for dahdi and want to compile  it with editing dkms.conf of dahdi in ubuntu 12.04. in which line I  must add "make subdirs+=" in the dkms.conf file ?

---

### Post by MG&amp;TL on 2012-12-30
> **rezaf said:**
> Hi, I have source files of a driver module for dahdi and want to compile  it with editing dkms.conf of dahdi in ubuntu 12.04. in which line I  must add "make subdirs+=" in the dkms.conf file ?

This isn't by any stretch a beginner's question.

Why do you want to use that particular method? From some brief research: [http://kb.digium.com/articles/Installation/Installing-DAHDI]("http://kb.digium.com/articles/Installation/Installing-DAHDI")

---

### Post by rezaf on 2013-01-02
Thanks but the link was not useful for my work because I installed the dahdi and asterisk completely and now want to add my custom device driver to dahdi and compile it with dahdi.

---

### Post by MG&amp;TL on 2013-01-02
> **rezaf said:**
> Thanks but the link was not useful for my work because I installed the dahdi and asterisk completely and now want to add my custom device driver to dahdi and compile it with dahdi.

I'm not an expert on the subject, but as you've got a custom device driver, wouldn't you just compile the module and then load it with insmod as usual? [http://www.tldp.org/LDP/lkmpg/2.6/html/x181.html](http://www.tldp.org/LDP/lkmpg/2.6/html/x181.html)

---

