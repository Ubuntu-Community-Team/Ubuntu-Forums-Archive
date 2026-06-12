---
title: "Fixing the python path"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by Nebelhom on 2013-06-26
Hi folks,

I recently switched my OS on my old laptop from Ubuntu to Xubuntu12.04 and ever since then I can't import certain libraries into python anymore. For some reason, many new modules are installed into

```
/usr/lib/python2.7/dist-packages
```

but my PYTHONPATH only contains the following paths

```
/usr/local/lib/python2.7/site-packages/setuptools-0.6c11-py2.7.egg
/usr/local/lib/python2.7/site-packages/mozdownload-1.6-py2.7.egg
/usr/local/lib/python2.7/site-packages/mozinfo-0.3.3-py2.7.egg
/usr/local/lib/python2.7/site-packages/Sphinx-1.2b1-py2.7.egg
/usr/local/lib/python2.7/site-packages/docutils-0.10-py2.7.egg
/usr/local/lib/python2.7/site-packages/Jinja2-2.6-py2.7.egg
/usr/local/lib/python2.7/site-packages/Pygments-1.6-py2.7.egg
/usr/local/lib/python2.7/site-packages/spyder-2.1.13.1-py2.7.egg
/usr/local/lib/python27.zip
/usr/local/lib/python2.7
/usr/local/lib/python2.7/plat-linux2
/usr/local/lib/python2.7/lib-tk
/usr/local/lib/python2.7/lib-old
/usr/local/lib/python2.7/lib-dynload
/usr/local/lib/python2.7/site-packages
```

I compared it to the paths on my desktop PC which has a ubuntu12.04 installation and there, the path does not include a single site-packages folder. I find this all very... strange. Is my installation somehow broken or got corrupted during the change? Is there an easy way to fix it? I would like to save myself the hassle of a OS reinstall.

Thanks a lot for all your help in advance.

---

### Post by dino99 on 2013-06-26
hey, 11.10 is dead since May ([https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases))
and comparing different distro releases is not the way to follow : too many changes done.

---

### Post by Nebelhom on 2013-06-26
@dino99: Thanks a lot for your reply. That is so weird. I just double-checked again. I wasn't thinking straight for the first post. Just typing the facts ;)

I just did an update and now it is given as Ubuntu 12.04. How bizarre... I edited the initial post to avoid confusion with the actual issue at hand.

Anyhow, the version is fine after all, so the PYTHONPATH issue remains. Have you got any idea regarding this?

Thanks for your help :)

---

### Post by Nebelhom on 2013-06-26
Ok, folks, I solved the problem. It turned out to be the same issue as here:

[http://askubuntu.com/questions/279866/python-module-not-found-after-manual-install](http://askubuntu.com/questions/279866/python-module-not-found-after-manual-install)

The python path was set to

```
/usr/local/bin
```  instead of to ```
/usr/bin/
```

Using the following line from the link above:

```
sudo rm -rf /usr/local/bin/python*
```

---

### Post by Nebelhom on 2013-06-27
Hmmm..., I want to mark this thread as solved, but I do not have the option in thread tools. Has this policy been abandoned or do we just edit the title now? I saw in the sticky that it is still advocated...

---

