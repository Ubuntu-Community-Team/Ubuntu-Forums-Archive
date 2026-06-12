---
title: "Installing software from tar.gz (tomboy 0.11)"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by monkley on 2008-08-17
Hello I have hardy installed and loving. However it comes with Tomboy 0.10 which appears to have a bug with webdav syncing. I think I read that 0.11 fixes that bug although I'm not sure where now! 

Anyway I am wondering if I can install Tomboy 0.11 from the link on the Intrepid packages page?
[http://packages.ubuntu.com/intrepid/tomboy](http://packages.ubuntu.com/intrepid/tomboy) 

Looking at the list of dependencies, I can see that 0.11 requires some newer versions than 0.10, e.g. libglib2.0-0  >= 2.17.6 which was >= 2.16.0 before.

So my question is can I install Tomboy 0.11 by compiling from the tarball without breaking y current setup?


PS Hardy rocks

---

### Post by tahina on 2008-08-17
Since no one else has answered yet, I'll try some guessing.

The version of libglib2.0-0 installed in Hardy is 2.16.4 and it looks like it's used by some important stuff (like gtk+), so you should set your mind at possibly breaking stuff...

I'd make backups and try some adventurous installations just for fun... :)

---

### Post by ShelJ on 2008-08-17
Hi there, here's a web page for you to look at  [http://linux.byexamples.com/archives/156/installing-from-tarballs/](http://linux.byexamples.com/archives/156/installing-from-tarballs/). I hope that it helps you.

---

