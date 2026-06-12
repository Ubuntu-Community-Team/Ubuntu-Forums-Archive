---
title: "[SOLVED] Displaying download progress in Python"
date: 2007-08-26
forum: Programming Talk
---

### Post by Ayuthia on 2007-08-26
Is there a way to display the progress of wget in Python?  I am calling wget via commands.getoutput, but the command does not display the progress until the command is complete.  Since some of the programs might take a little time to download, I would like to be able to show the progress of the download so that the user does not think that the program is in an endless loop.

---

### Post by Ayuthia on 2007-08-26
It looks like the subprocess.call (cmd, shell=True) will work for me.

---

### Post by Acglaphotis on 2007-08-26
How would you call it?

---

### Post by Ayuthia on 2007-08-26
I would have a function that will download a file.  For example:

```

import subproces

def download_file():
    successful_download=subprocess.call('wget -c http://mesh.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz')
    return successful_download
```

So when download_file() gets called, it will do the wget command and display the information that wget is sending.

Hope that makes sense.

---

### Post by Ayuthia on 2007-08-26
Oops.  Posted twice.

---

