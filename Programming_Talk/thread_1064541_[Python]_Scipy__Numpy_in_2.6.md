---
title: "[Python] Scipy / Numpy in 2.6"
date: 2009-02-08
forum: Programming Talk
---

### Post by elbarto_87 on 2009-02-08
Hi,

A course I am about to take on Python uses version 2.6 so I would like to install this on my laptop. As far as I can tell tho, most of the scientific modules such as numpy and scipy are not supported in 2.6. Does this mean that everyone out there using python 2.6+ will not be able to use these packages?


Regards Elbarto

---

### Post by .Maleficus. on 2009-02-09
Python 2.6 was just a release to make the transition to 3.0 smoother - the differences between it and 2.5 are extremely small.  Scipy and Numpy work well with 2.5 and since 2.5 code will run just fine with 2.6 (and vice versa), stay with 2.5.  You can always install 2.6 to say, /usr/local/bin and attempt to get Scipy and Numpy working without borking your 2.5 install, but honestly, until 3.0 is mainstream I'd just stick to 2.5.

---

### Post by elbarto_87 on 2009-02-09
Thank you for the reply. I will take you advice and stick with 2.5 for the time being.

Regards Elbarto

---

### Post by ssam on 2009-02-09
To see a list of whats new in python 2.6 see
[http://docs.python.org/whatsnew/2.6.html](http://docs.python.org/whatsnew/2.6.html)

for most usage there is very little difference. (if you are writing a large C module like scipy the differences become important, hence it taking a few months for them to make the changes)

---

