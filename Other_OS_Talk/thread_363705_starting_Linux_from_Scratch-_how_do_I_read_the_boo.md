---
title: "starting Linux from Scratch- how do I read the book while I am in the LiveCD??"
date: 2007-02-17
forum: Other OS Talk
---

### Post by billdotson on 2007-02-17
I booted the LiveCD and of course it was at a terminal and told me that the LFS-book-HMTL was in such folder so I cd'ed there and opened it, but since it was html I couldn't read half of it because it was in HMTL code.  How do I read it normally so I can actually use LFS to build a Linux distro?

Thanks

---

### Post by pay on 2007-02-17
I think it is ```
links /path/to/page.html
```

---

### Post by M_the_C on 2007-02-17
> **pay said:**
> I think it is ```
links /path/to/page.html
```
I thought it was 'lynx'?

Other options are to start the x-server and Xfce (which I haven't been able to do) and load it like a normal html document.

Or I use a PDA to view it on.  Lynx is good but it means a lot of switching back and forth.

---

### Post by confused57 on 2007-02-18
For LFS 6.2, type "startx", without quotes, at the prompt...then just open the web browser & you can just copy & paste...also, you might want to go to the LFS homepage & find the "Hint" for using the live cd to install LFS...the howto was written for 6.1, but the scripts are easily modified for 6.2:
[http://www.linuxfromscratch.org/hints/downloads/files/install-lfs-from-livecd.txt](http://www.linuxfromscratch.org/hints/downloads/files/install-lfs-from-livecd.txt)

this was relatively easy, with the scripts and copying & pasting.

I had installed LFS 6.0, typing everything in, which was rather tedious...

---

