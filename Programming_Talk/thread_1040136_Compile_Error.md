---
title: "Compile Error"
date: 2009-01-15
forum: Programming Talk
---

### Post by Stochastic on 2009-01-15
I don't really know if this is the right spot for this thread, but hopefully some insight can be found here.

I'm building the pyphat software found here: [http://phat.berlios.de/](http://phat.berlios.de/)
and I'm also attempting to package it for Jaunty.  When I build it on my Intrepid machine, everything goes off without a hitch.  When I build it in the pbuilder Jaunty environment, I get this build error: ```
.libs/phat_la-phat.o: In function `_wrap_phat_slider_button_get_threshold':
/tmp/buildd/pyphat-0.4.1/phat.c:1137: undefined reference to `PyInt_FromLong'
.libs/phat_la-phat.o: In function `_wrap_phat_pad_new':
/tmp/buildd/pyphat-0.4.1/phat.c:641: undefined reference to `PyArg_ParseTupleAndKeywords'
/tmp/buildd/pyphat-0.4.1/phat.c:648: undefined reference to `PyExc_RuntimeError'
/tmp/buildd/pyphat-0.4.1/phat.c:648: undefined reference to `PyErr_SetString'
.libs/phat_la-phat.o: In function `_wrap_phat_slider_button_set_threshold':
/tmp/buildd/pyphat-0.4.1/phat.c:1110: undefined reference to `PyArg_ParseTupleAndKeywords'
/tmp/buildd/pyphat-0.4.1/phat.c:1125: undefined reference to `_Py_NoneStruct'
/tmp/buildd/pyphat-0.4.1/phat.c:1113: undefined reference to `PyLong_Type'
/tmp/buildd/pyphat-0.4.1/phat.c:1113: undefined reference to `PyType_IsSubtype'
/tmp/buildd/pyphat-0.4.1/phat.c:1114: undefined reference to `PyLong_AsUnsignedLong'
/tmp/buildd/pyphat-0.4.1/phat.c:1119: undefined reference to `PyErr_Occurred'
/tmp/buildd/pyphat-0.4.1/phat.c:1115: undefined reference to `PyInt_Type'
/tmp/buildd/pyphat-0.4.1/phat.c:1115: undefined reference to `PyType_IsSubtype'
/tmp/buildd/pyphat-0.4.1/phat.c:1116: undefined reference to `PyInt_AsLong'

```

It keeps going with undefined reverence errors.  I'm thinking this is stemming from a missing library, a bad make instruction, or a newer version of gcc?  Anyone got any insight?  Thanks.

---

### Post by monkeyking on 2009-01-15
You need to elaborate on what what you have installed.

It looks like you are missing som python libraries,
do you have these installed?

have you done the
sudo apt-get install build-essential
?

---

### Post by Stochastic on 2009-01-15
This is the list of building requirements that I've sent to pbuilder (build-essential is automatically included).

libphat0-dev (>= 0.4.1), python-gtk2-dev, libgnomecanvas2-dev, libgtk2.0-dev, pkg-config, python2.5-dev, debhelper (>= 4), autotools-dev

---

