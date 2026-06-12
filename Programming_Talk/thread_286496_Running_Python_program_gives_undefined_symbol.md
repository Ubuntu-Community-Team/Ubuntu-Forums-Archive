---
title: "Running Python program gives undefined symbol"
date: 2006-10-27
forum: Programming Talk
---

### Post by jeffbarish on 2006-10-27
And here's another problem with the Python in Edgy: when I attempt to run Python programs that used to work, I often get the message:

undefined symbol: PyFPE_jbuf

This error message appears, for example, when I try to run pydoc.  Here's the traceback:

Traceback (most recent call last):
  File "/usr/local/bin/pydoc", line 5, in ?
    pydoc.cli()
  File "/usr/lib/python2.4/pydoc.py", line 2228, in cli
    serve(port, ready, stopped)
  File "/usr/lib/python2.4/pydoc.py", line 1917, in serve
    import BaseHTTPServer, mimetools, select
  File "/usr/lib/python2.4/BaseHTTPServer.py", line 76, in ?
    import mimetools
  File "/usr/lib/python2.4/mimetools.py", line 6, in ?
    import tempfile
  File "/usr/lib/python2.4/tempfile.py", line 33, in ?
    from random import Random as _Random
  File "/usr/lib/python2.4/random.py", line 44, in ?
    from math import log as _log, exp as _exp, pi as _pi, e as _e
ImportError: /usr/lib/python2.4/lib-dynload/math.so: undefined symbol: PyFPE_jbuf

---

### Post by jeffbarish on 2006-10-28
Mystery solved: After installing Ubuntu, I copied over the old /usr/local/bin.  It contained an old Python which was getting picked up before the correct one in /usr/bin.

---

