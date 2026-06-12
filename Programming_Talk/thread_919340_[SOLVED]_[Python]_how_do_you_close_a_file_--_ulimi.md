---
title: "[SOLVED] [Python] how do you close a file -- ulimit problem"
date: 2008-09-13
forum: Programming Talk
---

### Post by unutbu on 2008-09-13
It appears I can only write to 1019 files before my python script poops out.

Here is the program
[php]
#!/usr/bin/env python
import sys
import os
import tempfile

for idx in range(1025):
    outsock_path=tempfile.mkstemp()[1]
    print "%(outsock_path)s"%locals()
    try:
        outsock=open(outsock_path,'w')
    except IOError,err:
        print "IOError:",err
        print "Cannot write to %(outsock_path)s"%locals()
        print "idx=%(idx)s"%locals()
        sys.exit(1)
    finally:
        outsock.close()
        os.remove(outsock_path)
[/php]

I do use "outsock.close()", but that doesn't seem to do the trick.

Here is the error:
[php]
IOError: [Errno 24] Too many open files: '/tmp/tmpiy5qcd'
Cannot write to /tmp/tmpiy5qcd
idx=1019
[/php]
I believe this has to do with "ulimit -n":
[php]
% ulimit -n
1024
% help ulimit
    Ulimit provides control over the resources available to processes
    started by the shell, on systems that allow such control.  If an
    option is given, it is interpreted as follows:
...
        -n	the maximum number of open file descriptors
...
[/php]
If I add a "raw_input()" before the sys.exit(1) and do

[PHP]
ls -l /proc/PID/fd/[/PHP]

I can see lots of file descriptor links associated with my process:
[PHP]
% ls -l /proc/6972/fd/
total 0
lrwx------ 1 fancy fancy 64 2008-09-13 22:21 0 -> /dev/pts/0
lrwx------ 1 fancy fancy 64 2008-09-13 22:21 1 -> /dev/pts/0
lrwx------ 1 fancy fancy 64 2008-09-13 22:21 10 -> /tmp/tmpNKeBJ7 (deleted)
lrwx------ 1 fancy fancy 64 2008-09-13 22:21 100 -> /tmp/tmpEoc4Qf (deleted)
...
lrwx------ 1 fancy fancy 64 2008-09-13 22:21 998 -> /tmp/tmpJpsBWX (deleted)
lrwx------ 1 fancy fancy 64 2008-09-13 22:21 999 -> /tmp/tmp1yZDnx (deleted)
[/PHP]
How do I modify my python script so I do not hit up against this ulimit-ation?

---

### Post by unutbu on 2008-09-14
The problem was that tempfile.mkstemp() returns a file descriptor. I thought it was just an integer (it is) but it is associated with a file object which can be accessed through os.fdopen. 

This file object needs to be closed or you can end up with too many open files.

This works:
[PHP]#!/usr/bin/env python
import sys
import os
import tempfile
import shutil 

for idx in range(5000):
    (outfd,outsock_path)=tempfile.mkstemp()
    print "%(outsock_path)s"%locals()
    try:
        outsock=os.fdopen(outfd,'w')
    except IOError,err:
        print "IOError:",err
        print "idx=%s"%idx
        print "Cannot write to %(outsock_path)s"%locals()
        sys.exit(1)
    outsock.close()
    os.remove(outsock_path)
[/PHP]

---

