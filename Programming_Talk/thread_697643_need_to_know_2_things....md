---
title: "need to know 2 things..."
date: 2008-02-15
forum: Programming Talk
---

### Post by Choad on 2008-02-15
in python

1) how can i retrieve information about the host OS

2) how can i retrieve version information about a) linux binaries b) windows binaries?

---

### Post by amingv on 2008-02-15
1. What specific information do you need about the OS? The os module can provide some:
```
>>> import os
>>> help('os')
```

2. Not knowing a better method, I suggest using the "commands" module:
```
>>> import commands
>>> pyVer = commands.getoutput('python --version')
>>> print pyVer
Python 2.5.1
>>>    
```

Unfortunately, this module only works in Unix-like systems as far as I know.

---

### Post by Choad on 2008-02-16
thanks loads. it's a starting point at least i'll be able to get some kind of prototype built with this :)

edit: ohhhh idea... don't actually care about the version number, just if exe a and b are the same or not. could i not create some kind of hash to create a unique value for each exe?

are there any cases where this would not work? or is it safe to assume that exes of the same version will be bit-for-bit identical?

---

### Post by ruy_lopez on 2008-02-16
For the kernel version (linux):

```
uname -r
```

see 'man uname' for other flags.

Binaries sometimes respond to --version or -v (but sometimes -v is verbose).

You can look for strings in binaries using:

```
strings <binary>
```

this will show linkage info and error messages etc, maybe more.

s

---

### Post by ruy_lopez on 2008-02-16
```
md5sum <binary file>
```

will provide a checksum, if two files produce same checksum, they are the same.

EDIT: Just realised you need python solution:

```

from md5 import md5
fname = "binary_file"
s = md5(open(fname, "rb").read()).hexdigest()
print "md5 checksum: %s" % s

```

If the binaries are big you should do some buffering.

The odds of two checksums being the same for different files are pretty astronomical.

---

### Post by Choad on 2008-02-16
that's my point really... i was thinking maybe some companies may put unique serial codes in their binaries per download or something similar, which would throw off the checksum even if the binary is effectively identical. does this happen?

thanks for the examples tho :)

---

### Post by aks44 on 2008-02-16
> **Choad said:**
> maybe some companies may put unique serial codes in their binaries per download or something similar [...] does this happen?

It is very unlikely. Such a method demands too much maintenance:
- each time a new license is sold, it requires a rebuild
- similarly, whenever a new version is released they'd have to recompile the binary for each and every existing license


Granted this could happen, if the application developers are clueless, *and* if the company's management doesn't care wasting developers' time (thus money) without any benefit. As I said, quite unlikely (especially due to the second part ;)).

---

### Post by lnostdal on 2008-02-16
mh, you don't need to recompile or rebuild etc. to insert data (a serial, or whatever really) into a binary for each download (or for each user updating his version of his binary)

---

