---
title: "Installing python-igraph"
date: 2009-05-17
forum: Programming Talk
---

### Post by lbotha on 2009-05-17
I installed the following packages from [http://cneurocvs.rmki.kfki.hu/packages/binary/](http://cneurocvs.rmki.kfki.hu/packages/binary/)   :

libigraph_0.5.2_i386.deb
libigraph-dev_0.5.2_i386.deb
python-igraph_0.5.2_i386.deb
python-igraph-doc_0.5.2_i386.deb

but when I use the command (inside python) 

```
import igraph
```

all I get is:

```
ImportError: No module named igraph
```

So I tried locating the libigraph.so.0 file (like proposed by [http://stackoverflow.com/questions/834076/how-to-install-python-igraph-on-ubuntu-8-04-lts-64-bit/836948](http://stackoverflow.com/questions/834076/how-to-install-python-igraph-on-ubuntu-8-04-lts-64-bit/836948))

and it is located in:
```
/usr/lib/libigraph.so.0
```

and the path variable is set to
```
~$ echo $LD_LIBRARY_PATH 
:/usr/lib

```

Why does it still not work? Any suggestions?

---

### Post by paulohm on 2009-05-19
I had the exact same problem you had, but I managed to fix it.

The problem is that the package dumps the python igraph library into the wrong place! It dumps it into /usr/lib/python2.6/site-packages rather than /usr/lib/python2.6/dist-packages.

I got it to work by simply issuing the command:

```
sudo mv /usr/lib/python/2.6/site-packages/igraph /usr/lib/python/2.6/dist-packages/
```Hope this works for you too.

---

### Post by lbotha on 2009-05-19
> ```
sudo mv /usr/lib/python/2.6/site-packages/igraph /usr/lib/python/2.6/dist-packages/
```

Thank you so much, this solved the problem!

---

### Post by paulohm on 2009-05-19
I'm glad it worked out! I submitted a bugfix to the igraph bug tracker at [https://bugs.launchpad.net/igraph/+bug/378214](https://bugs.launchpad.net/igraph/+bug/378214) The maintainer already responded and said that he wasn't sure he could fix it, because this might be idiosyncratic to Ubuntu 9.04. Well, I hope other people find this thread in the meantime. Thus far, this thread is the sole Google hit for "ImportError: No module named igraph".

---

