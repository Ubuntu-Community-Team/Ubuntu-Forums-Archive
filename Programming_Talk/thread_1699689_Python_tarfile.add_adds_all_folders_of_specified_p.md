---
title: "Python tarfile.add adds all folders of specified path?"
date: 2011-03-04
forum: Programming Talk
---

### Post by kumoshk on 2011-03-04
I'm working with Python's tarfile module. From an arbitrary location, I need to be able to compress a directory and its contents in another arbitrary location. This works and all, but I'm running into the following problem:

Instead of just adding the folder and everything inside it (preserving only the structure within) it adds all the folders in the path that lead up to the folder I want to add!

Here's a simple example demonstrating what I'm doing:

```
import tarfile

tar = tarfile.open("myArchive.tar", "w")
tar.add("foo/bar")
tar.close()
```

What I want is a tar file that merely contains the 'bar' folder and all its contents (folders and all). However, what this does is add a folder called 'foo' containing the 'bar' folder with the 'bar' folder containing all its contents. In my current project, my path is a lot longer&#8212;so this is a lot more problematic.

Any ideas on how to fix this without a lot of overhead?

Thanks!

---

### Post by kumoshk on 2011-03-04
I found a solution. Do this instead:

```
import tarfile

tar = tarfile.open("myArchive.tar", "w")
tar.add("foo/bar", arcname="bar")
tar.close()
```

So, setting arcname is the solution (I don't know if it's the intended one, though, but I'm guessing so).

---

