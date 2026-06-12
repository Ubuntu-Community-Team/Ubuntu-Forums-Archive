---
title: "Python 3.1: How to view contents of tar.extractall"
date: 2009-08-21
forum: Programming Talk
---

### Post by bostonaholic on 2009-08-21
I want the command line to scroll through the files as they're being extracted, as if I were doing a normal extraction from the CLI.

```
> tar xzvf <archive.tar.gz>
Extracting file1
Extracting file2
.
.
.

```

Here is what my python method looks like so far.

```
def extract (self, file, dir):
    if not os.path.exists(dir):
        os.mkdir(dir)

    tar = tarfile.open(file, 'r:gz')
    tar.extractall(dir)
    tar.close()
```

Thanks.

---

### Post by unutbu on 2009-08-21
[PHP]#!/usr/bin/env python
import tarfile
tar=tarfile.open('test.tar.gz')
members=tar.getmembers()
for member in members:
    print('Extracting %s'%member.name)
    tar.extract(member)
[/PHP]

---

### Post by bostonaholic on 2009-08-21
> **unutbu said:**
> [PHP]#!/usr/bin/env python
import tarfile
tar=tarfile.open('test.tar.gz')
members=tar.getmembers()
for member in members:
    print('Extracting %s'%member.name)
    tar.extract(member)
[/PHP]

I didn't think of doing it that way.  Works wonderfully, thanks!

---

