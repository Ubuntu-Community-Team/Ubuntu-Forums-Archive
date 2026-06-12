---
title: "How to make a .patch file?"
date: 2009-11-01
forum: Packaging and Compiling Programs
---

### Post by NoBugs! on 2009-11-01
I've tried making a diff on an ubuntu program to make a small change, but when I put the file in ./debian/patches directory of the source, it won't compile. When I run dpkg-buildpackage it starts, but gives error:
"Trying patch debian/patches/file.patch at level 1 ... 0 ... 2 ... failure."
The log shows:
"can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:"
....

What program do I have to use to make valid .patch files??

---

### Post by SevenMachines on 2009-11-02
Probably the most likely option is as it says, patches in debian patches are stripped at -p1, so your patch should have file paths in them that are relative to the top package directory when the first directory is stripped. i.e
package-directory/src/somefile

Try using diff with -ruN options. for example
diff -ruN original-package-directory fixed-package-directory >mychanges.patch

---

