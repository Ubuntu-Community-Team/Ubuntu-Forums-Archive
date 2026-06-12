---
title: "How Can I Alter Parameter File In Script?"
date: 2009-05-09
forum: Programming Talk
---

### Post by jsmidt on 2009-05-09
I need to run this command:

```
synfast params.ini
```

Where params.ini is a parameter file this code was designed to read which looks like this:

```
infile=bestcl.fits
outfile=out1.fits

```
  It is a very complex program so altering how it works is out of the question. (So it has to read this file, no way around that.  No command line arguments, etc.)

What I need is a script that will run the above command 100 times where each time it runs the outfile=out1.fits in the params.ini file increments each time: outfile=out1.fits, outfile=out2.fits outfile=out3.fits, etc...

Does anyone know any script that can do this?  Run the command 100 times while altering this flag in the params file each time?  Thanks.

---

### Post by unutbu on 2009-05-09
[PHP]#!/usr/bin/env python
from subprocess import Popen,PIPE,STDOUT
params='''infile=bestcl.fits
outfile=out%s.fits
'''
for num in range(1,101):
    print num,
    open('params.ini','w').write(params%num)
    Popen('synfast params.ini', shell=True, stdout=PIPE, ).communicate()
[/PHP]
Save this in ~/bin. Suppose you call it ~/bin/hunrun.py
Make it executable:```

chmod 755 ~/bin/hunrun.py
```
Run it like this:```

hunrun.py
```

---

### Post by jsmidt on 2009-05-09
Thank you so much.

---

