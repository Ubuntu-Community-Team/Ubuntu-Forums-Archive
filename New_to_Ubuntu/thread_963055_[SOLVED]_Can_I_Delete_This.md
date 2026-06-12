---
title: "[SOLVED] Can I Delete This?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-10-29
Hello again!
I can't believe it: Ubuntu 8.10 will finally be released tomorrow! Speaking of which, I was wondering how to delete past, outdated versions. 
Here is what I mean: When I start my computer, it gives me 7 options to choose from. The start-up screen looks like this:

"Ubuntu 8.04.1, kernel 2.6.24-21-generic
Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest 86+
Other Operating Systems:
Windows Vista/Longhorn (loader)
Windows Vista/Longhorn (loader)"

I am assuming that the "Ubuntu 8.04.1, kernel 2.6.24-21-generic" is the new version and that "Ubuntu 8.04.1, kernel 2.6.24-19-generic" is the outdated. 

How do I delete the outdated system and its recovery mode? When the new Ubuntu 8.10 is released, do I do the same thing to delete the current Ubuntu 8.04?

Thanks for your time.

Take care,
RedStarYellowSun

---

### Post by ad_267 on 2008-10-29
Those are previous linux kernels and are there just in case a new one stops working properly.

You can search for linux-headers and linux-image in synaptic package manager (under System - Administration) and remove the outdated packages. (Make sure you don't remove any of the 2.6.24-21 versions)

When you upgrade to 8.10 the old kernels will all be removed automatically because they aren't in the Intrepid repositories.

---

### Post by aktiwers on 2008-10-29
There is a program called cruft-remover that cleans all that stuff up (and more) for you. Check it out.

---

### Post by jpeddicord on 2008-10-29
> **aktiwers said:**
> There is a program called cruft-remover that cleans all that stuff up (and more) for you. Check it out.

Though you'll have to upgrade to Intrepid to get that first! :D

---

### Post by aktiwers on 2008-10-29
> **jacobmp92 said:**
> Though you'll have to upgrade to Intrepid to get that first! :D

Oops... forgot about that. Sorry.

---

### Post by RedStarYellowSun on 2008-10-29
Wow, that was fast.
Thanks!
You guys surely beat Vista Forums. I just posted the problem and I already received a reply.
Thanks again!

Take take,
RedStarYellowSun

---

