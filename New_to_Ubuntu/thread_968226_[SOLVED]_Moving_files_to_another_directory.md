---
title: "[SOLVED] Moving files to another directory"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-02
I have some pictures that are in several sub-directories and would like to move the all pictures in each sub-directory into one main directory.

Have looked [here](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=BasicCommands) and used 'info mv' (in Terminal) etc and can't see a way to move more than one file at a time.

Is there a "wild-card" that I can use to move several files at once?

Something like this:

```
mv SubDirectoryContainingFilesToMove/"wildcard" NewDirectory
# or this
mv "all of these in" SubDirectoryContainingFilesToMove NewDirectory
```

Where the quotes are whatever option/command I need to use to do this task.

---

### Post by davec64 on 2008-11-02
You're nearly there!

```
mv folder1/*.txt folder2/

```

Where * is the wild card and .txt is the file type.

Alternatively if you just want to move everything (not a specific file type, drop the extension (in the case of the example the ,txt):

```
mv folder1/* folder2/

```

---

### Post by boof1988 on 2008-11-02
> **davec64 said:**
> You're nearly there!

```
mv folder1/*.txt folder2/

```

Where * is the wild card and .txt is the file type.

Alternatively if you just want to move everything (not a specific file type, drop the extension (in the case of the example the ,txt):

```
mv folder1/* folder2/

```

Thanks...  I'll try these out.

---

