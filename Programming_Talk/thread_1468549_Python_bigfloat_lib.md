---
title: "Python bigfloat lib"
date: 2010-05-01
forum: Programming Talk
---

### Post by Jbike on 2010-05-01
Does anyone know how to get the Bigfloat library to work with Python ? I checked synaptic and [http://packages.python.org/bigfloat/#installation](http://packages.python.org/bigfloat/#installation) for ideas.... I believe that I have MPFR as well as the GMP libraries installed from synaptic, though it is difficult to know exactly which pkgs should be installed since there are several with each name. I get errors every time I try to import the lib with either :  from BigFloat import * or import Bigfloat ...   Both yield errors. 

Thanks, 
Jbike

---

### Post by Bachstelze on 2010-05-01
You need to download the package from [here](http://pypi.python.org/pypi/bigfloat/0.1.1). Extract the tarball and do

```
sudo python setup.py install
```

You will need [font=monospace]libmpfr-dev[/font].

---

### Post by Jbike on 2010-05-01
Thanks so much it works like a charm. Interesting that it wasn't already in synaptic somewhere... I believe that it should be included. I have just one more question ... Why does bigfloat only work in python V2.6 and not V3.1? The same was true with vpython and I believe pygame? Have these pkg's just not caught up with the latest version(s) of python? Sounds (so far) to me that only V2.6 should be used. 

Thanks so much!
Jbike

---

### Post by Bachstelze on 2010-05-02
> **Jbike said:**
> Thanks so much it works like a charm. Interesting that it wasn't already in synaptic somewhere... I believe that it should be included.

I had a look at the source, maybe the reason it isn't included is that the source files do not have a comment at the top indicating which license they fall under (yes, that could be a reason for not including it). I will investigate this (meanwhile I have made a package for it in my PPA, it's awaiting building at the moment).

> **Jbike said:**
> Have these pkg's just not caught up with the latest version(s) of python? Sounds (so far) to me that only V2.6 should be used.

Seems so. The [font=monospace]test_bigloat.py[/font] file, for example, contains stuff like

```
values = [2, 3L, 1.234, BigFloat('0.678'), BigFloat('nan'),
```

The [font=monospace]3L[/font] is not valid in Python 3.

---

### Post by Jbike on 2010-05-03
Thanks so much for the extra info... Others may also appreciate the detail.  Consider this case closed, and I will try add this via the PPA and synaptic when I install 10.04 on the other machine. 

:)
Jbike

---

