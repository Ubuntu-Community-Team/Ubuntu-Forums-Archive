---
title: "using a filename list in a python script"
date: 2009-01-17
forum: Programming Talk
---

### Post by gabesword on 2009-01-17
Hello.  I'm trying to run a python script to cat some .avi files together.  Here is what the script looks like.

```
#!/usr/local/bin/python

import os, subprocess

dirin = raw_input('enter the directory ')
filelist = os.listdir(dirin)

subprocess.call('cat ' + filelist + ' > test.avi", cwd=dirin, shell=True)
```
Here is the error I get while running: TypeError: cannot concatenate 'str' and 'list' objects

Does anybody have an idea on how I could accomplish this?

---

### Post by lykwydchykyn on 2009-01-17
try using this:
```

subprocess.call('cat ' + " ".join(filelist) + ' > test.avi", cwd=dirin, shell=True)

```

---

### Post by eightmillion on 2009-01-17
> **gabesword said:**
> Hello.  I'm trying to run a python script to cat some .avi files together.  Here is what the script looks like.

```
#!/usr/local/bin/python

import os, subprocess

dirin = raw_input('enter the directory ')
filelist = os.listdir(dirin)

subprocess.call('cat ' + filelist + ' > test.avi", cwd=dirin, shell=True)
```
Here is the error I get while running: TypeError: cannot concatenate 'str' and 'list' objects

Does anybody have an idea on how I could accomplish this?

Here's a couple other unrelated ideas. You might want to make sure that dirin is actually a directory, and also build a list of just the avi files in the directory like so.

```
#!/usr/local/bin/python

import os, subprocess

dirin = raw_input('enter the directory ')
if not os.path.isdir(dirin):
    print '%s is not a valid directory' % str(dirin)
    exit(1)
else:
    filelist = [ i for i in os.listdir(dirin) if os.path.splitext(i)[1].lower() == '.avi' ]

subprocess.call('cat ' + " ".join(filelist) + ' > test.avi", cwd=dirin, shell=True)
```

---

### Post by ghostdog74 on 2009-01-17
> **gabesword said:**
> Hello.  I'm trying to run a python script to cat some .avi files together.  Here is what the script looks like.

```
#!/usr/local/bin/python

import os, subprocess

dirin = raw_input('enter the directory ')
filelist = os.listdir(dirin)

subprocess.call('cat ' + filelist + ' > test.avi", cwd=dirin, shell=True)
```
Here is the error I get while running: TypeError: cannot concatenate 'str' and 'list' objects

Does anybody have an idea on how I could accomplish this?
why can't you just simply do this with the shell
```

# cat *.avi > test.avi

```

---

### Post by gabesword on 2009-01-18
Thanks for the suggestions.  That should do the trick.

@ghostdog74

I could use *.avi but I'm really trying to learn python more than I am trying to get quick results.

---

### Post by ghostdog74 on 2009-01-18
if that's your case, then there's really "no point" in trying to call external shell commands when you can do them ALL in python.

---

