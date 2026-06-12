---
title: "debconf questions only asked in terminal, not in GUI frontends"
date: 2021-07-20
forum: Packaging and Compiling Programs
---

### Post by mcdope1337 on 2021-07-20
Hi,

I've got a problem with building a package that I simply can't solve. Looking for hints, or maybe even a solution... 

We are talking about [https://github.com/mcdope/pam_usb](https://github.com/mcdope/pam_usb) here. 

My package is working fine, debconf is working too. But only if installed on the cli. As soon as gdebi, synaptic or "whatever graphical frontend" is used to install the package none of the questions in config will be asked and they will appear as skipped in postinst.

Nothing I could find in the manpages or by Google solved this so far and this is my very first package... I have given up by now and accepted it as a fact but maybe someone has an idea?


Thanks in advanced for any input

---

