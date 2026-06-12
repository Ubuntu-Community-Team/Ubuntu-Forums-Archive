---
title: "Whitespaces in makefile-path"
date: 2012-06-25
forum: Packaging and Compiling Programs
---

### Post by Pille456 on 2012-06-25
Hi,

I want to compile a program, which brings its own makefile. The Makefile looks something like:
```

# ...
all:
  @$(MAKE) -C ../../SomePath/MorePath SomeOptions
  @$(MAKE) -C SomePath/MorePath SomeOptions
  # ... 

```

After compiling, make copies the program in "../Build/". Make itself runs fine, but the copy-progress does not work, because there are whitespaces in the path. SomePath/MorePath does not contain any whitespaces, but the folder in which both both are placed contain whitespaces (so the '..' in the path)

Is there a way to edit the makefile to handle theses spaces or do I have to use another path/folder?

Greetings

Pille456

---

### Post by Ravi Amlani on 2012-07-05
No... there is no way if and only if your problem is because of white spaces in the source folder. Because in DOS we've facility to put the path between single quotes. But here its advisable to remove white spaces.

---

