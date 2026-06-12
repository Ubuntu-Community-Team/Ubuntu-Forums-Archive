---
title: "Mono Question"
date: 2010-02-11
forum: Programming Talk
---

### Post by coverslide on 2010-02-11
So I did some mono stuff maybe a year ago, but I've forgotten much of it. I've tried it up again, but when I try to compile a simple Hello World program, I get a bunch of CS0234 errors:

```
error CS0234: The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?
```Now I know I can manually add these assemblies with the -r: option, but I don't remember having to do that a year ago. Plus a lot of the examples and tutorials I see online simply say:

```
mcs example.cs
```I wonder if there is a config option missing or environment variable or **something **that tells the compiler where to locate these assemblies?

Thanks in advance.

---

### Post by SemiBuz on 2010-02-12
[http://packages.ubuntu.com/search?keywords=winforms&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=winforms&searchon=names&suite=karmic&section=all) ?

---

