---
title: "HOWTO: apt-offline ?"
date: 2005-01-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Bdfy on 2005-01-23
I want install packages from Ubuntu's repositories but my computer have not internet 
Can I know depends for this package ( in my current system ) and download its manually in not debian system ?

---

### Post by ken_devon on 2005-01-23
You can find the dependencies for a package with apt-cache showpkg (or synaptic).
One way of installing the packages without a direct connection would be to download them from the repository using a web broswer or something, copy them over to your Ubuntu machine, and install them with 
sudo dpkg -i *package files...* .

There're  other ways - have a look at 
[this part of the APT HOWTO](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages) 

and the apt-offline package.

---

