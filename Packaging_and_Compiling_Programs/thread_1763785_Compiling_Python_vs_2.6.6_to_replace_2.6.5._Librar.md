---
title: "Compiling Python vs 2.6.6 to replace 2.6.5. Library linking and various issues."
date: 2011-05-20
forum: Packaging and Compiling Programs
---

### Post by excetara2 on 2011-05-20
I am compiling Python 2.6.6 so it includes googles tcmalloc library because having issues with memory allocation in the malloc library. I have python compiled no dramas.

I can't figure out the best way to integrate it with the system. It sets it as default because in /usr/local/bin but then my dist-packages seem to be broken. I also then have issues with installing things because can't find setuptools etc...

Do the 2.6.5 versions of setuptools and wxPython (or any packages from debs) work fine with the compiled version? Or would these have to be recompiled for python 2.6.6 meaning I couldn't use anything from the software channel. Anyway if anyone knows whats best let me know. I had to recompile numpy,scipy,matplotlib already. This wasn't hard as I use the development versions anyway. I would rather not have to download and compile all. Or a way to make pip/easy_install use the new version of python.

---

