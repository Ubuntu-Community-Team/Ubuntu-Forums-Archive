---
title: "Signal acquisition and online analysis of electrophysiological data."
date: 2013-04-28
forum: New to Ubuntu
---

### Post by aher31416 on 2013-04-28
I have been using labview for signal acquisition and originlab for analysis but I moved recently to ubuntu and I am looking for an alternative that combines both features. If you could recommend me something that lets me perform the analysis immediately after acquisition would be great.

---

### Post by tgalati4 on 2013-04-28
tgalati4@Mint14-Extensa ~ $ apt-cache search comedi
libcomedi-dev - Development library for Comedi
libcomedi0 - Library for Comedi
libgnuradio-comedi3.6.1 - gnuradio comedi instrument control functions
python-comedilib - Python wrapper for Comedilib

[http://www.comedi.org/hardware.html](http://www.comedi.org/hardware.html)

I've used Kubios for heart rate variability analysis:  [http://kubios.uef.fi/](http://kubios.uef.fi/)

National Instruments has a large library of C routines for handling their hardware, so with a little searching, you can often find academic research programs/software that is published.  You might have to read a few dissertations to find it.  You would need to modify it for your purposes and compile it.

---

