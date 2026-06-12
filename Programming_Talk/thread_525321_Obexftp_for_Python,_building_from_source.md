---
title: "Obexftp for Python, building from source"
date: 2007-08-14
forum: Programming Talk
---

### Post by MrJavalava on 2007-08-14
Hey I'm building obexftp from the source however I'm having a few issues with it.
I'm using the obexftp-0.22-rc6 at the moment, since the 0.20 has a few bugs in it.
The reason why I'm not using the obexftp in the repository is due to the fact I can't find any python libraries in it... Anyhu

For those who are having issues with compiling:
[http://ubuntuforums.org/showthread.php?t=206033&highlight=cannot+find+Python+include+path](http://ubuntuforums.org/showthread.php?t=206033&highlight=cannot+find+Python+include+path) --> first

The parameters I've used to install it are:

./configure --disable-ruby --disable-perl --disable-tcl
make
make install

It's fine so far, however, when I import obexftp in python:
[B]>>> import obexftp
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "usr/local/lib/python2.5/site-packages/obexftp/__init__.py", line 7, in <module>
ImportError: libobexftp.so.0: cannot open shared object file: No such file or directory
>>> 
[/B]
I get this nifty error.

A quick search with locate gives me:
[B]locate libobexftp.so
/usr/local/lib/libobexftp.so.0
/usr/local/lib/libobexftp.so
/usr/local/lib/libobexftp.so.0.2.0
[/B]

So there must be something else bothering me... I'm using Python2.5 from the repository. I reckon there is something that isn't put right. I've followed the scarce guide from [http://dev.zuckschwerdt.org/openobex/wiki/ObexFtpInstalling](http://dev.zuckschwerdt.org/openobex/wiki/ObexFtpInstalling) 

Now there is one guy who had the same error, BUT, he didn't want to use the library for development:
[http://www.linuxforums.org/forum/suse-linux-help/68109-obexftp-problem.html](http://www.linuxforums.org/forum/suse-linux-help/68109-obexftp-problem.html)

There must be a link or something that is broken as far as I can see, but i don't really know..

---

### Post by pmasiar on 2007-08-14
Why you installing from sources? Project website recommends using version from ubuntu repository, why it is not good enough?

---

### Post by eng_akyq on 2009-05-23
I am using Ubuntu and Python but when I run python script with obexftp I got the follwing error
```

IDLE 1.1.5      ==== No Subprocess ====
>>> import obexftp
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in ?
    import obexftp
ImportError: No module named obexftp
>>> 

```


However I define all obexftp by synaptic. I have downloaded and applied ,but the problem is still found as shown above.
How can I define obexftp with python.

---

### Post by eng_akyq on 2009-05-24
I have found a solution to my problem by disable the binding of obexftp with Perl,Ruby and TCL but I don't know how to do these disables in Ubuntu environment.
Any ideas about that
Thanks in advance

---

