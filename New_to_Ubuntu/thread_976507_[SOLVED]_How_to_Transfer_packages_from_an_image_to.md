---
title: "[SOLVED] How to: Transfer packages from an image to reinstalled Ubuntu"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by melrokz on 2008-11-09
Hi! I'm Melvin from India.
I have a slow internet connection and am not able to upgrade Ubuntu to 8.10. So, I now have Ubuntu 7.10 with lots of downloaded 'n installed packages that I'd like to transfer to Ubuntu 8.10 after installing it. 
I use Clonezilla to make an image of 7.10 and stored on my hdd.
Plz tell me how to transfer packages without downloading them again!!!

---

### Post by PriceChild on 2008-11-09
Packages are created for individual distributions. I recommend only running packages built for Intrepid on Intrepid etc. rather than those built for Hardy.

If you want to ignore this, find /var/cache/apt/archives/ on the old image and install packages from there.

---

### Post by mapes12 on 2008-11-09
> If you want to ignore this, find /var/cache/apt/archives/ on the old image and install packages from there.

Alternatively, if you do decide to give it a go: System>Administration>Synaptic Package Manager then search for "aptoncd". Here's the web page: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

