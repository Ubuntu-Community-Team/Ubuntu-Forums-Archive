---
title: "python-xpcom problems"
date: 2008-03-04
forum: Programming Talk
---

### Post by vrc on 2008-03-04
Hi everybody,

I want to use python-xpcom package to make Gecko download an HTML file, parse it and execute any JavaScript that may be present. But I ran into problems already on setup.
The package was installed properly (immediately after xulrunner package), and I googled out some python-xpcom tutorials, but it appears I'm doing something wrong, because I can't get even simplest local-file access scripts to work.
This is my code:
```
import xpcom._xpcom
import xpcom
from xpcom import components
from xpcom.components import interfaces

filecls = components.classes["@mozilla.org/file/local;1"].createInstance()
print filecls; print
file = filecls.queryInterface(interfaces.nsILocalFile);
print file; print
file = file.initWithPath("/home/vrc/Download/PyXPCOM/foobar.txt")
print file
```
And this is the output when I run the script:
```
Registering 'moz.pyloader.1' (libpyloader.so)
<XPCOM component '@mozilla.org/file/local;1' (with no class info)>

<XPCOM component '@mozilla.org/file/local;1' (with no class info)>

None
```
File foobar.txt exists
Tutorials say that the result of first "print file" should be "<XPCOM interface 'nsILocalFile'>". So, either I'm doing something wrong, or there is a bug in python-xpcom module.
Any ideas?
TIA

---

### Post by PaulFr on 2008-03-08
I do not know much about XPCOM, but the object **file** that you get after the steps you posted, is valid and does respond to queries like ```
>>> file.fileSize
345L
>>> file.isSymlink()
False
``` You can examine all the methods available using **file.__dict__**

For reference, here are the entries file responds to: > 'moveTo' 'exists' 'lastModifiedTimeOfLink' 'getRelativeDescriptor'
  'isDirectory' 'createUnique' 'path' 'isExecutable' 'append' 'normalize'
'parent' 'leafName' 'create' 'contains' 'diskSpaceAvailable' 'copyTo'
'QueryInterface' 'permissionsOfLink' 'directoryEntries' 'isHidden'
'DIRECTORY_TYPE' 'setRelativeDescriptor' 'isSymlink' 'clone'
'copyToFollowingLinks' 'equals' 'persistentDescriptor' 'fileSize'
  'isSpecial' 'followLinks' 'lastModifiedTime' 'permissions' 'reveal'
  'initWithFile' 'target' 'launch' 'remove' 'NORMAL_FILE_TYPE' 'isReadable'
'fileSizeOfLink' 'initWithPath' 'isFile' 'isWritable' 'appendRelativePath'
Note that delete is not in this list (even though I saw this in some PyXPCOM tutorials).

---

### Post by vrc on 2008-03-10
Hm, yes, thanks, it didn't occur to me to check the contents of __dict__. Heh :)

---

### Post by UV-Ray on 2009-06-03
For others, who wondering how this code can work, just replace
**file = file.initWithPath("/home/vrc/Download/PyXPCOM/foobar.txt")**
with
**file.initWithPath("/home/vrc/Download/PyXPCOM/foobar.txt")**
and file will be valid xpcom object.

---

