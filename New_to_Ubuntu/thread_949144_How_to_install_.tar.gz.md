---
title: "How to install .tar.gz"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by PCPimp on 2008-10-15
I am very new to linux I'm a MCSE :0 Gotta love Microsoft. hehe. :) I do understand how to unpack (unzip) them I move to the dir and type ./configure and nothing.... what is another way to install .tar.gz files?

Thanks

---

### Post by ramjet_1953 on 2008-10-15
What is the package that you are trying to install?
Chances are it is already in the repositories.
If not, do a search for the name of the program with a .deb suffix.

Failing that, compiling is not just a matter of installing.
You need to install the "build-essential" package as a starter.

```
sudo apt-get install build-essential
```

Then you will need to sort out the dependencies that are required for the package, install them also and you will also probably need to install the .dev packages associated with those dependencies.

I would also recommend that you install the "checkinstall" package.

```
sudo apt-get install checkinstall
```

This allows you to create a .deb package, which makes it much easier to manage the program, as it will appear in Synaptic.

All of the above is not hard, but you need to learn how to do it by crawling, before you walk.

Regards,
Roger:cool:

---

