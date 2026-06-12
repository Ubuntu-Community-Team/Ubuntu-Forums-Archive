---
title: "mit-scheme will not install. error message: &quot;"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by montana111 on 2008-09-17
im trying to get the mit-scheme development environment to install on my new ubuntu installation.  when i use synaptic or apt i get errors.   the synaptic error is something like " package/install is not satisfiable. Error: libmcrypt4"

what did i do wrong? is there a way to get scheme on my computer? what do i do?

---

### Post by jamesrl on 2008-09-17
It seems like there was an error installing the package libmcrypt4 that mit-scheme depends on to install.  Can you try installing from the command line with 

```
sudo apt-get install mit-scheme
```

the error message there may be more verbose, and explain why it is giving an error on installation.

Similarly you could try manually installing libmcrypt4 yourself within synaptic, and see what the error installing it is.

---

