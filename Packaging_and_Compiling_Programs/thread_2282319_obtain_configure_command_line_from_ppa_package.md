---
title: "obtain configure command line from ppa package"
date: 2015-06-13
forum: Packaging and Compiling Programs
---

### Post by bannndi on 2015-06-13
Hi everybody,

I am wondering, if it can be accomlished? Say, I have installed version of PHP 5.4 from [https://launchpad.net/~ondrej/+archive/ubuntu/php5-oldstable](https://launchpad.net/~ondrej/+archive/ubuntu/php5-oldstable), and I just want to learn how to compile it from source and to install it by my self. 

Is there a way to get this information ? I assume, it should be available even from installed package, not only from compiled source. 

So what I want is such "$ ./configure ... ... ALL THOSE OPTIONS ... ... " line for mentioned above ppa package. :)


PS - phpinfo() function doesnot show this information in section "Configure Command", seems like it was disabled on author's purpose.
Comparing the two phpinfo() outputs - is my last resort.
Search in web did not give me answers.

---

### Post by ian-weisser on 2015-06-14
Yes, but...
There are TWO types of packages, and only one will help you.

The *pre-built (binary/published) packages* at [https://launchpad.net/~ondrej/+archive/ubuntu/php5-oldstable](https://launchpad.net/~ondrej/+archive/ubuntu/php5-oldstable) won't help you. They don't include any make or configure information source; only the finished (built) files and configurations.

The *source packages* at [https://launchpad.net/~ondrej/+archive/ubuntu/php5-oldstable/+packages](https://launchpad.net/~ondrej/+archive/ubuntu/php5-oldstable/+packages) have more of the information you want.

This is an oversimplification, and there are lots of exceptions and corner cases, but it's the basic answer to your question.

---

### Post by bannndi on 2015-06-15
> **ian-weisser said:**
> 
The *source packages* at [https://launchpad.net/~ondrej/+archive/ubuntu/php5-oldstable/+packages](https://launchpad.net/~ondrej/+archive/ubuntu/php5-oldstable/+packages) have more of the information you want.


Seems like in list from this link there is source-package "php5 - 5.4.42-1+deb.sury.org~precise+1", - so - is there a way to get information I want from it?

---

### Post by ian-weisser on 2015-06-15
Sure,
No magic to it.
Browse through the source until you find the configure information or makefile.

---

### Post by bannndi on 2015-06-16
> **ian-weisser said:**
> Browse through the source until you find the configure information or makefile.

I'll try, thank you.

---

