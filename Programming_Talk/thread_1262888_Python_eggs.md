---
title: "Python eggs"
date: 2009-09-10
forum: Programming Talk
---

### Post by sphh on 2009-09-10
Hello, dear gurus!

Until now I gave the easy_setup/setuptools program suite a wide berth. But today I installed one egg with it and now I have the mess!

So what is the problem:


[LIST=1]
[*]I installed a python module (Sphinx that is) with ```
sudo python setup.py install --prefix /usr/local/
``` (after downloading, extracting, building it).
[*]Since that did not work, I removed every already copied file and directory.
[*]Then I wanted to install the egg from the web with ```
sudo easy_install <URI>
```
[*]What a bummer! I get the nice error :```
error: can't create or remove files in install directory

The following error occurred while trying to add or remove files in the
installation directory:

    [Errno 2] No such file or directory: '/usr/local/lib/python2.6/dist-packages/test-easy-install-21179.write-test'

The installation directory you specified (via --install-dir, --prefix, or
the distutils default setting) was:

    /usr/local/lib/python2.6/dist-packages/

This directory does not currently exist.  Please create it and try again, or
choose a different installation directory (using the -d or --install-dir
option).

```
[/LIST]
Yes, it is true, this directory does not exist any more. But I haven't told easy_install to use this directory. That is I have not told it now.

So where does easy_install/setuptools store these locations that I can remove it!

I use Ubuntu 9.04.

I googled around, had a look into the source code but could not figure out how to get rid of it!

I promise to keep my fingers away from setuptools!!

Many thanks for any hint in the right direction,
Stephan

---

