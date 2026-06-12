---
title: "Software Center is Broken"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-05-03
I've had nothing but problems lately trying to download a couple of apps, like LMMS and Google Earth. Been getting all these weird error messages about how ia32-lib can't be installed. And now the Software Center is broken.

It doesn't matter which app I click on, I only get the following error messsage.

Any chance there's a fix for this problem?

---

### Post by cortman on 2012-05-03
Hi, can you install from the command line?

```
sudo apt-get update
sudo apt-get install kile
```

for instance.
If you can successfully install from CLI, your best bet is probably to reinstall the USC.

```
sudo apt-get install software-center --reinstall
```

---

### Post by Curtis6767 on 2012-05-03
I've gone into the package manager and checked and unchecked various sources and now the software center seems to be working. I can't remember its default settings, but I may now be close. When I open the software center, I'm no longer getting the weird error message from earlier.

However, and regardless of what I do, I cannot install ia32-lbs either through the software center or via the terminal.

Any ideas on that?

Thanks

---

### Post by beboylips on 2012-05-04
This issue is called "multiarch" and is a new way to run 32 bit apps on 64bit. Doesn't work well yet apparently. Apps that require the packages ia32-lbs won't work until they are upgraded by their developers to work with multiarch. Until then, use either 32bit ubuntu with kernel-pae (to use all the ram) or run the 64bit versions of programs (and compile from source if unavailable).

-Beboy

---

### Post by Curtis6767 on 2012-05-04
> **beboylips said:**
> This issue is called "multiarch" and is a new way to run 32 bit apps on 64bit. Doesn't work well yet apparently. Apps that require the packages ia32-lbs won't work until they are upgraded by their developers to work with multiarch. Until then, use either 32bit ubuntu with kernel-pae (to use all the ram) or run the 64bit versions of programs (and compile from source if unavailable).

-Beboy

Thanks for the reply. I am not totally sure, but it does appear at the moment that the Software Center is working, so I'm going to mark this thread solved.

---

