---
title: "[Python] TypeError when changing last-modified on file"
date: 2011-08-17
forum: Programming Talk
---

### Post by Frozen Forest on 2011-08-17
I keep getting TypeError when changing last modified time on files that this script create, but why?
[PHP]
            name = os.path.splitext(filename)[0]
            fd = open(path + filename, 'r')
            file_content = fd.read()
            fd.close()
            f = open(path + name + '.txt', 'w')
            f.write(file_content)
            f.close()
            mtime = os.path.getmtime(path + filename)
            os.utime(f,(time.time(),mtime))
[/PHP]

```

  File "./ToText.py", line 25, in main
    os.utime(f,(time.time(),mtime))
TypeError: coercing to Unicode: need string or buffer, file found

```

---

### Post by Arndt on 2011-08-17
> **Frozen Forest said:**
> I keep getting TypeError when changing last modified time on files that this script create, but why?
[PHP]
            name = os.path.splitext(filename)[0]
            fd = open(path + filename, 'r')
            file_content = fd.read()
            fd.close()
            f = open(path + name + '.txt', 'w')
            f.write(file_content)
            f.close()
            mtime = os.path.getmtime(path + filename)
            os.utime(f,(time.time(),mtime))
[/PHP]

```

  File "./ToText.py", line 25, in main
    os.utime(f,(time.time(),mtime))
TypeError: coercing to Unicode: need string or buffer, file found

```

utime wants the path to the file (i.e., its name), not the file object.

---

### Post by regala on 2011-08-17
> **Frozen Forest said:**
> 
```

  File "./ToText.py", line 25, in main
    os.utime(f,(time.time(),mtime))
TypeError: coercing to Unicode: need string or buffer, file found

```

can't you just **read** ?

---

