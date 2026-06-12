---
title: "Altering PATH in packages"
date: 2010-08-25
forum: Packaging and Compiling Programs
---

### Post by J&#7885;hn on 2010-08-25
Hi Everyone

I've compiled a program from source and to comply with our typical way of doing things have installed it in /opt/progname. I'm now rolling it up into a .deb file, but because of the non standard path I'm a bit stuck.

My question is how do I add /opt/progname permanently to the system path in the postinst file and have it removed again in the postrm file?

I found this snippet of code for removal but I suspect it'll only apply to the present session

```
PATH=$(echo $PATH | sed -e 's;:\?/opt/progname;;' -e 's;/opt/progname:\?;;')
```This program is for Hardy 64bit, but I'll also be packaging for Lucid.

Thanks for any wisdom you can impart

J&#7885;hn

---

### Post by J&#7885;hn on 2010-08-26
Ah. Found it's easier to create a script softlinking to all the necessary files from /usr/local/bin instead, and then removing them when the package is uninstalled.

Thanks to anyone who perused this.

---

