---
title: "Create Patch for Directory Containing Binary Files"
date: 2013-01-12
forum: Programming Talk
---

### Post by dodle on 2013-01-12
I know how to use the [color=red]diff[/color] command to create patches for source. But diff seems to bypass binary files. Is there a way to include differences in binary files?

Example:
```
/old/foo/bar.txt
/old/foo/bar.png

/new/foo/bar.txt
/new/foo/bar.png
```

---

### Post by ofnuts on 2013-01-13
No, because it is usually pointless. For a PNG for instance, even a very small color change will change all the bytes in the file. So you usually end up replacing th whole binary anyway.

---

### Post by Bachstelze on 2013-01-13
> **ofnuts said:**
> No, because it is usually pointless. For a PNG for instance, even a very small color change will change all the bytes in the file. So you usually end up replacing th whole binary anyway.

That is true for PNGs, but binary patches can still be useful for other types of files.

@dodle: That's not what diff is for; use something like xdelta.

---

### Post by dodle on 2013-02-11
Thanks for the info :). I realize now that what I was trying to do is unecessary for source revision control systems.

---

