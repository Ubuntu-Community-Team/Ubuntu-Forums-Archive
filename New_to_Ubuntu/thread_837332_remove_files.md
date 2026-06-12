---
title: "remove files"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by szaqlon on 2008-06-22
I am trying to remove all files for g15. I use locate to find quite a few, but then when I try to remove them it says no such file or directory. All of the files have g15 with something else before and after it, none are just g15. So I have tried *g15*, but nothing. How can I remove all the files that are shown on locate?

---

### Post by the_doc on 2008-06-22
Locate will return the complete path to a file that meets your search criteria.  In order to delete those files you would first have to navigate to the correct directory and use the **rm** command, or go via the GUI.

It would be possible to write a script that used the output of locate as a list of files to delete, but that's more work obviously!

EDIT:

You could of course supply the entire path to the **rm** command, which is presumambly what you're not doing if you are getting that error message.

---

### Post by diaa on 2008-06-22
If you are sure you want to remove those files, you can try the following command after replacing the first part(before the pipe |) with the locate of your choice

```
locate \*.tmp|xargs rm -v
```

the trailing -v will make it output the names of the files being removed, note that this can't be undone, files will be removed completely not into the trash bin.

---

