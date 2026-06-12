---
title: "[SOLVED] Firefox 3 installation procedure?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by sdim on 2008-07-29
Hi,everyone.
I have downloaded the Firefox 3.tar.bz2 file and I can't seem to be able to install it.I decompressed it,and tried _cd Desktop_ and _cd Firefox_ and then _./configure _,but nothing.It seems that it can't be installed this way.
I tried through Synaptic,but all I found is Firefox 3 beta 4,which I've installed,but is this the same as the standard Firefox 3 edition running now?
Any bit of help is appreciated.
Thanks.

---

### Post by tuxxy on 2008-07-29
Yes its the same one, 3.01

---

### Post by jemate18 on 2008-07-29
If you are using hardy, it is in the repository try this:
$sudo apt-get install firefox-3.0 

You can also view all packages in the ubuntu repository
[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

-jemate18

---

### Post by aysiu on 2008-07-29
You can't ./configure and all that because it isn't source code - it's a precompiled binary.

This should help you, though:
[http://www.psychocats.net/ubuntu/firefox#terminal](http://www.psychocats.net/ubuntu/firefox#terminal)

---

### Post by sdim on 2008-07-31
Thanks for all the answers.
I'm running Mint,which is based on Gutsy.

---

### Post by aysiu on 2008-07-31
> **sdim said:**
> Thanks for all the answers.
I'm running Mint,which is based on Gutsy.
Instructions for Ubuntu should also work for Linux Mint, since Mint is just based on Ubuntu anyway.

---

