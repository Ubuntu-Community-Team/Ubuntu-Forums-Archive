---
title: "install gmpy2 python module"
date: 2014-10-09
forum: Programming Talk
---

### Post by partloer on 2014-10-09
I am trying to install gmpy2 which I followed the directions [https://gmpy2.readthedocs.org/en/latest/intro.html#installing-gmpy2-on-unix-linux](https://gmpy2.readthedocs.org/en/latest/intro.html#installing-gmpy2-on-unix-linux) however I get an ImportError: No module name gmpy2

I am running python 2.7.6 on Ubuntu 14.04

---

### Post by ian-weisser on 2014-10-09
I would install the python-gmpy or python3-gmpy package from the Software Center instead of trying to manually install.

Er, if you decide to try the packages, be sure to first manually uninstall the gmpy that you manually installed.
Otherwise, you might make rather a mess.

---

### Post by partloer on 2014-10-10
Thanks ian-weisser that worked!

---

