---
title: "Can't launch Spyder,IDE for Python"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by nns2006 on 2011-09-15
Hi, I have been using spyder for Python. After upgrading from 10.10 to 11.04, I am not able to use this. On launch it gives me this output in terminal. 
 
> ~$ spyder
Traceback (most recent call last):
  File "/usr/local/bin/spyder", line 4, in <module>
    import pkg_resources
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2671, in <module>
    working_set.require(__requires__)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 654, in require
    needed = self.resolve(parse_requirements(requirements))
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 552, in resolve
    raise DistributionNotFound(req)
pkg_resources.DistributionNotFound: spyder==2.0.12


What does it mean? and how to make it work again.

Thank you.

---

### Post by nns2006 on 2011-09-17
I am still looking for an answer to this. 

Thank you

---

### Post by Pynalysis on 2011-10-04
Eclipse IDE with PyDev plugin provides a similar environment to Spyder - might be interested in trying that.

---

### Post by trashie on 2012-02-19
Hi Pynalysis,

Your error is just telling you that, although you have the script /usr/local/bin/spyder that is supposed to actually launch spyder, you seem to miss spyder library in the python path.

How did you install Spyder?

Could you give us the result of the following command:
```
ls /usr/lib/python2.7/dist-packages/
```

You should have something (a directory actually) called like:
"spyder-2.X.X-py2.7.egg"

If not, then you don't have spyder installed as a regular ubuntu python package. Check this place then:
```
ls /usr/local/lib/python2.7/dist-packages/
```
If you still don't have a spyder version in there, you need to install it.

A very easy way to do this is:
```
sudo easy_install spyder
```

Good luck!

PS: if you did install spyder yourself, eg. by compiling it, you may still fix the problem you're having by looking for the place where you actually did install spyder. In that case, you don't need to install it again.

---

