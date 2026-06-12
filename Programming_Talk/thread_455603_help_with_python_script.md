---
title: "help with python script"
date: 2007-05-26
forum: Programming Talk
---

### Post by nix4me on 2007-05-26
Hi,

I am using the following script to print a list if the folders in a dir that are less than a week old.  Its working great however im trying to add the date of each folder to the output.  I would like the date to be in a human readable format, not seconds.

Here is the code:

```
import os
import time
for x in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
	print x
```

Any help would be appreciated.

nix4me

---

### Post by WW on 2007-05-26
You can use time.ctime():
```

import os
import time
for x in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
    print "%-20s %s" % (x, time.ctime(os.path.getmtime(x)))

```

---

### Post by nix4me on 2007-05-26
Nice!  thanks for the reply.  Works perfectly.

nix4me

---

### Post by nix4me on 2007-05-26
ok, i've folded this into my xchat script and now im having problems defining multiple sections.  I want 2 triggers, 1 for each of 2 dirs.  So when i use trigger 1, it lists the new folders in a folder.  When i use trigger 2, it lists the new folders in a second folder.

For somereason the second def is not working...i think the 2 sections are interfering with each other.

Here is the code:
```
#!/usr/bin/env python
__module_name__ = "newfolders"
__module_version__ = "0.1"
__module_description__ = "New Folders script for xchat, written by nix4me."
import os
import time
import xchat
import commands
def newscripts(word, word_eol, userdata):
    os.chdir("/mnt/fileserver/SCRIPTS")
    for x in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
        print "%-20s %s" % (x, time.ctime(os.path.getmtime(x)))
def newxchat(word, word_eol, userdata):
    os.chdir("/mnt/fileserver/XCHAT")
    for y in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
        print "%-20s %s" % (y, time.ctime(os.path.getmtime(y)))
#trigger   
xchat.hook_command("scripts", newscripts)
xchat.hook_command("xchat", newxchat)
#info
print "newfolders.py loaded"
```

Any ideas how to get the second def to work?

---

### Post by dwblas on 2007-05-27
Can't you just pass the dir name to the function and do it twice?  I don't know anything about xchat, but that is the "normal" way to do it.  Is that what xchats' USERDATA  parameter is?

---

### Post by nix4me on 2007-05-28
Its 2 different dirs.  Im tyring to have /scripts show me one dir and /xchat show me another.  The first one works, the second doesnot.

nix4me

---

### Post by cwaldbieser on 2007-05-30
> **nix4me said:**
> ok, i've folded this into my xchat script and now im having problems defining multiple sections.  I want 2 triggers, 1 for each of 2 dirs.  So when i use trigger 1, it lists the new folders in a folder.  When i use trigger 2, it lists the new folders in a second folder.

For somereason the second def is not working...i think the 2 sections are interfering with each other.

Here is the code:
```
#!/usr/bin/env python
__module_name__ = "newfolders"
__module_version__ = "0.1"
__module_description__ = "New Folders script for xchat, written by nix4me."
import os
import time
import xchat
import commands
def newscripts(word, word_eol, userdata):
    os.chdir("/mnt/fileserver/SCRIPTS")
    for x in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
        print "%-20s %s" % (x, time.ctime(os.path.getmtime(x)))
def newxchat(word, word_eol, userdata):
    os.chdir("/mnt/fileserver/XCHAT")
    for y in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
        print "%-20s %s" % (y, time.ctime(os.path.getmtime(y)))
#trigger   
xchat.hook_command("scripts", newscripts)
xchat.hook_command("xchat", newxchat)
#info
print "newfolders.py loaded"
```

Any ideas how to get the second def to work?

I don't have xchat, so I am not able to test this:
```

#!/usr/bin/env python
__module_name__ = "newfolders"
__module_version__ = "0.1"
__module_description__ = "New Folders script for xchat, written by nix4me."
import os
import time
import xchat
import commands

def xchat_list_dir_callback(word, word_eol, userdata):
    dir_to_list = None
    if word[0].lower() == "scripts":
        dir_to_list = "/mnt/fileserver/SCRIPTS"
    elif word[0].lower() == "xchat":
        dir_to_list = "/mnt/fileserver/XCHAT"
    elif word[0].lower() == "listdir" and len(word) >= 2:
        dir_to_list = word_eol[1]
    else:
        return None
    
    for x in [file for file in os.listdir(dir_to_list) if time.time()-os.path.getmtime(file) < 604800]:
        print "%-20s %s" % (x, time.ctime(os.path.getmtime(x)))
    return None

#trigger   
xchat.hook_command("scripts", xchat_list_dir_callback)
xchat.hook_command("xchat", xchat_list_dir_callback)
#info
print "newfolders.py loaded"

```

So basically, if you type "/scripts", the xchat_list_dir_callback function is called and should list your scripts folder.  If you type "/xchat", the same function is called, but it lists your xchat folder.  Finally, if you type "/listdir /home/nix4me" it should list the contents of your home folder.

This should work even if the path contains spaces like "/listdir /home/nix4me/file with spaces.txt".

I hope it works!

---

### Post by nix4me on 2007-05-30
Thats an interesting implementation.  I will try it out.  I actually got it working like this too:

```
#!/usr/bin/env python
__module_name__ = "newfolders"
__module_version__ = "0.1"
__module_description__ = "New Folders script for xchat, written by nix4me."
import os
import time
import xchat
import commands
def newscripts(word, word_eol, userdata):
    os.chdir("/mnt/fileserver/SCRIPTS")
    xchat.command("say 12This weeks newest SCRIPTS:")
    for x in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
        xchat.command("say %-20s %s" % (x, time.ctime(os.path.getmtime(x))))
    return xchat.EAT_ALL
def newxchat(word, word_eol, userdata):
    os.chdir("/mnt/fileserver/XCHAT")
    xchat.command("say 12This weeks newest XCHAT:")
    for y in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
        xchat.command("say %-20s %s" % (y, time.ctime(os.path.getmtime(y))))
    return xchat.EAT_ALL
def newcode(word, word_eol, userdata):
    os.chdir("/mnt/fileserver/CODE")
    xchat.command("say 12This weeks newest CODE:")
    for z in [file for file in os.listdir(os.curdir) if time.time()-os.path.getmtime(file) < 604800]:
        xchat.command("say %-20s %s" % (z, time.ctime(os.path.getmtime(z))))
    return xchat.EAT_ALL
#trigger   
xchat.hook_command("scripts", newscripts)
xchat.hook_command("xchat", newxchat)
xchat.hook_command("code", newcode)
#info
print "newfolders.py loaded"
```

nix4me

---

