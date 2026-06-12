---
title: "slowing down output"
date: 2009-03-06
forum: Programming Talk
---

### Post by nix4me on 2009-03-06
My script works great but it floods me off IRC.  It looks into a dir and prints the folders/files which are under a week old.  It works great, but if the dir gets alot of files in a week, the output floods me off IRC.  Is there anyway to integrate a timer into it?  Or just a way to slow down the output?

```
#!/usr/bin/env python
__module_name__ = "newfolders"
__module_version__ = "0.1"
__module_description__ = "New Folders script for xchat, written by nix4me."
# Load the necessary modules
import os
import re
import time
import xchat
import commands
option = {}
# newest code in chdir since last 7 days - triggered by a local /newcode
def newcode(word, word_eol, userdata):
    os.chdir("/mnt/storage1/code")
    for x in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
        xchat.command("say %-20s %s" % (x, time.ctime(os.path.getmtime(x))))
    return xchat.EAT_ALL
xchat.hook_command("code", newcode)

```

Any help would be greatly appreciated.

---

### Post by WW on 2009-03-06
The [time](http://docs.python.org/library/time.html) module has a [sleep](http://docs.python.org/library/time.html#time.sleep) function.  You could sleep a bit before sending a new message.

---

### Post by nix4me on 2009-03-06
Tried that.  It only delays the start of the command.  It does not delay in between each post.

Thanks for the suggestion though.

---

