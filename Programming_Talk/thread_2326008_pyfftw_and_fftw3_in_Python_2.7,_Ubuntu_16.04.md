---
title: "pyfftw and fftw3 in Python 2.7, Ubuntu 16.04"
date: 2016-05-27
forum: Programming Talk
---

### Post by Kubilay_Ovacikli on 2016-05-27
Hi!

I have been trying to run FFTW (3.3.4) alongside pyfftw (0.10.1) in Spyder (2.3.9), python version : 2.7.11, Ubuntu 16.04. Cython (0.23) is set without any problems.

 I tried to install both packages manually and through repositories. In all cases, that is the error I get from the console: 
 [COLOR=#0000ee][FONT=Ubuntu Mono]_File "/usr/lib/python2.7/dist-packages/pyfftw/__init__.py", line 16, in <module>_[/FONT][/COLOR]

 [COLOR=#cd0000][FONT=Ubuntu Mono]    from .pyfftw import ([/FONT][/COLOR]
 [COLOR=#cd0000][FONT=Ubuntu Mono]ImportError: /usr/lib/python2.7/dist-packages/pyfftw/pyfftw.x86_64-linux-gnu.so: undefined symbol: fftwl_plan_with_nthreads

[/FONT][/COLOR][FONT=&amp]and when I try importing pyfftw in IPython[/FONT][COLOR=#cd0000][FONT=Ubuntu Mono]
ImportError                               Traceback (most recent call last)
<ipython-input-1-c7c3740380ed> in <module>()
----> 1 import pyfftw

/usr/lib/python2.7/dist-packages/pyfftw/__init__.py in <module>()
     14 from .version import version as __version__
     15 
---> 16 from .pyfftw import (
     17         FFTW,
     18         export_wisdom,

ImportError: /usr/lib/python2.7/dist-packages/pyfftw/pyfftw.x86_64-linux-gnu.so: undefined symbol: fftwl_plan_with_nthreads


[/FONT][/COLOR][FONT=&amp]Your recommendations are highly appreciated, thanks in advance![/FONT][COLOR=#cd0000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by hgomersall on 2016-06-02
Are you able to give more information on this.

Does the relevant FFTW lib file exist - probably something like: [FONT=courier new]/usr/lib/x86_64-linux-gnu/libfftw3l_threads.so.3.4.4[/FONT]

If so, is the [FONT=courier new]fftwl_plan_with_nthreads[/FONT] symbol shown with:[FONT=courier new]

nm -D /usr/lib/x86_64-linux-gnu/libfftw3l_threads.so.3.4.4

Finally, if those both look fine, what does the following report:

ldd /usr/lib/python2.7/dist-packages/pyfftw/pyfftw.x86_64-linux-gnu.so

(specifically, the reference to libfftw3l_threads.so)[/FONT]

---

### Post by Kubilay_Ovacikli on 2016-06-02
[COLOR=#000000][FONT=Ubuntu Mono]First of all, thanks for your reply! 

To begin with, when I issue (Python)

print '\n'.join(sys.path)[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]returns:

 [COLOR=#000000][FONT=Ubuntu Mono]/usr/local/lib/python2.7/dist-packages/Cython-0.23-py2.7-linux-x86_64.egg[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/python2.7[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/python2.7/plat-x86_64-linux-gnu[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/python2.7/lib-tk[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/python2.7/lib-old[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/python2.7/lib-dynload[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/local/lib/python2.7/dist-packages[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/python2.7/dist-packages[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/python2.7/dist-packages/PILcompat[/FONT][/COLOR]
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/python2.7/dist-packages/gtk-2.0


Then, I run all the commands you recommended and the reported output is attached, though I am not sure if they seem the way they're supposed to...
[/FONT][/COLOR]

---

### Post by hgomersall on 2016-06-03
This seemed to be an issue with the debian packages. See: [https://github.com/pyFFTW/pyFFTW/issues/112](https://github.com/pyFFTW/pyFFTW/issues/112)

It should be fixed upstream shortly and propagate into Ubuntu as and when.

An interim solution is to use the packages on PyPI or from github. Just to a `pip install pyfftw` and you should get it.

---

### Post by Kubilay_Ovacikli on 2016-06-07
Now it works just as it should... Great, thanks!

---

