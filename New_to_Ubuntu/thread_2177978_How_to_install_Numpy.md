---
title: "How to install Numpy"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by JohnDogg on 2013-10-01
Hello,

I am trying to install to Numpy on Python 2.7 (the version which comes with Ubuntu 12.10),
until now without success.

I have tried in  a linux shell:

$ sudo apt-get install python-numpy python-scipy

and I got the answer: "python-numpy" has no installation candidate

I have also tried to download the source code for numpy directly from SciPy.org.
It also did not work. 

Can somebody tell me what the problem may be? I suppose that some package, which
numpy depends on, is missing. If necessary I can provide additional information.

Thanks for the help

JohnDogg

---

### Post by lukeiamyourfather on 2013-10-01
The de facto way to install would be with pip which is a package manager built into Python. The next would be with the operating system package manager. You can find packages for pip from PyPI.

[https://pypi.python.org/pypi](https://pypi.python.org/pypi)

I've never tried but I'm sure Ubuntu has a NumPy package, it just might be under a different name. Try 'apt-cache search numpy' and see what you get.

---

### Post by JohnDogg on 2013-10-10
Hello,

the installation of "pip" worked out but, unfortunately, I did not manage to install numpy by using "pip". Some errors did appear, it seemed that some needed packages were missing.

I noticed that there was some blockade and because of this I was not able to install anything from the web. By taking a look at some other thread of a guy having similar problems, I put in following commands:

1) sudo rm /var/lib/apt/lists/* -vf
2) sudo apt-get update && sudo apt-get upgrade

(do not know what it does :<) , but it seems to have solved the general blockade problem)

At the end, I installed synaptic (as an administrator) and I installed numpy from inside it (also as an administrator). Now it is working...

Thank you very much anyway,

JohnDogg

---

