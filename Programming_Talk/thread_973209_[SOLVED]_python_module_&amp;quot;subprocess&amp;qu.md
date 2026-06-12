---
title: "[SOLVED] python module &amp;quot;subprocess&amp;quot; problem"
date: 2008-11-06
forum: Programming Talk
---

### Post by giuspen on 2008-11-06
i'm trying to substitute some functions that the python library defines obsolete with the adviced ones (from the subprocess module) but i've stucked with one substitution that throws error and i can't understand why, if anybody can help is very appreciated.

i try to substitute:
```
destination_root = os.popen(choose_destination).read().replace('\n', '')
```
that is working good ("choose_destination" is a shell command string),
with:
```
destination_root = subprocess.Popen(choose_destination, stdout=PIPE, shell=True).communicate()[0].replace('\n', '')
```
that is not working.

---

### Post by raf_kig on 2008-11-06
Could you maybe be a bit more specific on what 'not working' means?

Regards

raf

---

### Post by giuspen on 2008-11-06
> **raf_kig said:**
> Could you maybe be a bit more specific on what 'not working' means?

Regards

raf

hi raf and thanks for reply,
the code throws an exception... this code is part of an extension of nautilus i'm working on, that u can find on [http://open.vitaminap.it/en/linux_developments.htm](http://open.vitaminap.it/en/linux_developments.htm)

regards,
giuseppe.

---

### Post by unutbu on 2008-11-06
[PHP]#!/usr/bin/env python
import subprocess
choose_destination = 'zenity --title="Choose the destination" --file-selection --directory'
destination_root = subprocess.Popen(choose_destination, stdout=subprocess.PIPE, shell=True).communicate()[0].replace('\n', '')
print destination_root
[/PHP]
The above code works for me. Perhaps try it and see if it works for you. The only difference between the above and what you've written is that PIPE was replaced with subprocess.PIPE.

If this does not fix the error, please post the exception that you are getting, such as,

```
Traceback (most recent call last):
  File "test.py", line 6, in <module>
    destination_root = subprocess.Popen(choose_destination, stdout=PIPE, shell=True).communicate()[0].replace('\n', '')
NameError: name 'PIPE' is not defined
```

---

### Post by giuspen on 2008-11-06
> If this does not fix the error, please post the exception that you are getting...

thanks a lot it works... I didn't imagine that PIPE was defined in the module "subprocess".
with this extensions i'm writing i have some difficulties to debug, I don't know how to see the standard output from the shell, so I lose many time for trivial things. I tried to launch nautilus from the shell and then use the extensions but nothing. 

regards,
giuseppe.

---

