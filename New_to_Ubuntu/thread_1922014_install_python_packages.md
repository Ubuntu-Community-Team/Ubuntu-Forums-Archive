---
title: "install python packages"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by cliuari on 2012-02-07
I want to install networkx without root previlege. I follow some suggestions from the sources from the internet. I download the package and unpack it into a folder, open a terminal, then use " python setup.py install --user ". It doesn't work. It " cannot open file setup.py ". When I use " easy_install ", it said "easy_install" is not defined.
 
My system is Ubuntu 11.04 with python2.7.1. 
 
Anyone can help on this? Thanks.

---

### Post by Rodney9 on 2012-02-07
networkx is available in Synaptic.

Rodney

---

### Post by cortman on 2012-02-07
> **cliuari said:**
> I want to install networkx without root previlege.

I do NOT recommend this at all- yes, it's possible to force install into your /home directory, but you lose a lot of error checking functionality with dpkg and apt, and it's a fast ticket to dependency misery.
Why don't you have root on the computer if it's yours?

---

### Post by cliuari on 2012-02-08
Thanks for the two replies. Following your suggestions, I installed the package with root previllege through Synaptic. It works.

---

