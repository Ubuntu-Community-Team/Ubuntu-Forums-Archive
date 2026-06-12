---
title: "libncurses-dev in no repository"
date: 2005-02-07
forum: Repositories &amp; Backports
---

### Post by credo on 2005-02-07
Hey all,

I have just installed Warty. I need to get my wireless card working, so I need to install a new kernel.

When I run "make menuconfig", it tells me I need ncurses-dev. I try searching for it, and it isnt in any of my repositories (the stock Warty + multiverse). 

How can I get this package?

Cheers.

---

### Post by alainhenry on 2005-02-07
You could add the debian repositories.  Look at  [http://ubuntuguide.org](http://ubuntuguide.org) for more details if you need more information on how to do it.

Alain

---

### Post by az on 2005-02-07
No.  Do not do that.

libncurses5-dev provides libncurses-dev


apt-cache show libncurses5-dev.

---

