---
title: "How do you force setup.py to use X compiler?"
date: 2009-10-04
forum: Packaging and Compiling Programs
---

### Post by jsmidt on 2009-10-04
I have a few python packages I have downloaded that have c code that needs to be compiled.  When I type ```
python setup.py build
``` I get the gcc doing the compiling.

Normally you want this.  However, I want to try to compile these packages with the intel compilers.  When I try like this ```
python setup.py build -c=icc
``` I get this error: ```
don't know how to compile C/C++ code on platform 'posix' with '=icc' compiler
```

I've tried changing icc with intel or doing -compiler or adding -f  and, etc... and I always get the same error.

Is there any way to edit setup.py to force it to use "icc" as the compiler?  While I'm at it, can I edit setup.py to force it to use different flags?

Thanks.

---

### Post by diesch on 2009-10-04
Does
```

python setup.py build -c icc

```
work?

---

### Post by jsmidt on 2009-10-04
> **diesch said:**
> Does
```

python setup.py build -c icc

```
work?

Unfortunately I still get this: "don't know how to compile C/C++ code on platform 'posix' with 'icc' compiler".  But thanks.

---

### Post by ArneBab on 2012-03-02
> **jsmidt said:**
> Unfortunately I still get this: "don't know how to compile C/C++ code on platform 'posix' with 'icc' compiler".  But thanks.

Sorry for raising this thread from the dead. If you don&#8217;t have it fixed now, you should be able to get it running by importing numpy.distutils.intelccompiler in your setup.py

(I just had the same problem and this thread came up when I searched. Well, and: [http://xkcd.com/979/](http://xkcd.com/979/))

A slightly more elaborate solution which only requires numpy, if you actually want to use the intel compiler, looks like this:

setup.py:
```
&#8230;
if "intel" in sys.argv or "icc" in sys.argv:
    try: # make it compile with the intel compiler
        from numpy.distutils import intelccompiler
    except ImportError:
        print "Compiling with the intel compiler requires numpy."
        raise
&#8230;
```

[IMG]http://imgs.xkcd.com/comics/wisdom_of_the_ancients.png[/IMG]
[http://xkcd.com/979/](http://xkcd.com/979/)

---

### Post by nothingspecial on 2012-03-02
> **ArneBab said:**
> Sorry for raising this thread from the dead. 

Please don't.

Thank you.

Closed.

---

