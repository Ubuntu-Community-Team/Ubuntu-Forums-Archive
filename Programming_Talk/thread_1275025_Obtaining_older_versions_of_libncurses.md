---
title: "Obtaining older versions of libncurses"
date: 2009-09-25
forum: Programming Talk
---

### Post by cmnorton on 2009-09-25
Where can I get older versions of libncurses. I am running Ubuntu 9.04 and am getting these errors when compiling:

/usr/bin/ld: skipping incompatible /usr/lib/libncurses.so when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.a when searching for -lncurses

Specifically, I need libncurses4, and cannot find it in synaptic or through apt-get.

---

### Post by lloyd_b on 2009-09-25
> **cmnorton said:**
> Where can I get older versions of libncurses. I am running Ubuntu 9.04 and am getting these errors when compiling:

/usr/bin/ld: skipping incompatible /usr/lib/libncurses.so when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.a when searching for -lncurses

Specifically, I need libncurses4, and cannot find it in synaptic or through apt-get.

It used to be available, up until Hardy.  What you can do is go [here]("http://packages.ubuntu.com/source/hardy/ncurses4.2") and download the sources, and then compile it yourself.

Note: I would strongly recommend against installing it into /usr - it'll probably conflict with the ncurses5 you have installed.  You *should* be able to install it in /usr/local safely, though.

Lloyd B.

---

### Post by Zugzwang on 2009-09-25
> **cmnorton said:**
> Where can I get older versions of libncurses. I am running Ubuntu 9.04 and am getting these errors when compiling:

/usr/bin/ld: skipping incompatible /usr/lib/libncurses.so when searching for -lncurses
/usr/bin/ld: skipping incompatible /usr/lib/libncurses.a when searching for -lncurses


I think that if you get this error while *linking* ("ld" will not be called when compiling), it is more likely that you are trying to link against 32-bit libraries when trying to produce a 64-bit binary or the other way around. Is that possible?

---

### Post by cmnorton on 2009-10-01
> **lloyd_b said:**
> It used to be available, up until Hardy.  What you can do is go [here]("http://packages.ubuntu.com/source/hardy/ncurses4.2") and download the sources, and then compile it yourself.

Note: I would strongly recommend against installing it into /usr - it'll probably conflict with the ncurses5 you have installed.  You *should* be able to install it in /usr/local safely, though.

Lloyd B.

I could not find anything at your "here" link.

---

### Post by lloyd_b on 2009-10-01
> **cmnorton said:**
> I could not find anything at your "here" link.

??? Did you not get to the page "Source Package: ncurses4.2 (4.2-10.1) [universe]"?  Towards the bottom of the page are three download links.  I'm not entirely sure what the ".dsc" file is.  The "...orig.tar.gz" is a gzipped archive of the base sources for ncurses 4.2, and the "...diff.gz" file is a patch to bring it up to 4.2-10.1.

Lloyd B.

---

