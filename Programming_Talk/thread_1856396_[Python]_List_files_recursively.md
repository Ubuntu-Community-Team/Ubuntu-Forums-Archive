---
title: "[Python] List files recursively"
date: 2011-10-08
forum: Programming Talk
---

### Post by blazemore on 2011-10-08
Is there any way I can list all files underneath a particular directory, similar to the way Find works?

Preferably with access to the full filename.

So if I call listFiles("dir1")
I get

/dir1/foo
/dir1/dir2/bar

for example.

It doesn't have to be cross-platform; it can even depend on UNIX find command. Is this possible?

---

### Post by Barrucadu on 2011-10-08
The algorithm will be like this:

```
ListDir (path):
    For all entries in path:
        Print (entry)
        If entry is a directory:
            ListDir (entry)

```

Look into the os module.

---

### Post by ofnuts on 2011-10-08
> **blazemore said:**
> Is there any way I can list all files underneath a particular directory, similar to the way Find works?

Preferably with access to the full filename.

So if I call listFiles("dir1")
I get

/dir1/foo
/dir1/dir2/bar

for example.

It doesn't have to be cross-platform; it can even depend on UNIX find command. Is this possible?
See "os.listdir(...)" or "os.walk(...)"

---

### Post by simeon87 on 2011-10-08
If the directory structure is known, you can also use glob. For example, this will print all files one directory deep:

```
import glob
for f in glob.glob("*/*.*"):
    print f
```

You can vary the glob pattern to search where you want. See the [glob documentation]("http://docs.python.org/library/glob.html").

---

