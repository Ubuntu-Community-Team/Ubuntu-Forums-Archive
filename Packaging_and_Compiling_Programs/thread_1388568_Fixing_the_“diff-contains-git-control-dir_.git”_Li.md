---
title: "Fixing the “diff-contains-git-control-dir .git” Lintian error message"
date: 2010-01-23
forum: Packaging and Compiling Programs
---

### Post by knipknap on 2010-01-23
I am trying to Debianize a package and Lintian produces the following errors:

```
$ lintian ../mypackage_0.1.7-gaa12c77_source.changes 
W: mypackage source: native-package-with-dash-version
W: mypackage source: diff-contains-git-control-dir .git
```

Any idea how to fix the second warning? According to the maintainer docs, the -i switch of debuild or dpkg-buildpackage should be used, however, they don't seem to make any difference. None of the following fixes the issue:

```
dpkg-buildpackage -i'.git'
dpkg-buildpackage -i'/.git'
dpkg-buildpackage -i'.git*'
dpkg-buildpackage -i'\.git.*'
```

(The same behavior with debuild, of course.)

For the reference, the debian/ directory is here:

[http://github.com/knipknap/Gelatin/tree/master/debian/](http://github.com/knipknap/Gelatin/tree/master/debian/)

---

### Post by SevenMachines on 2010-01-23
try
$debuild -S -i -I

the -i -I options are passed to dpkg-source with default sensible exclusion options, it works here for .git warnings

**from man dpkg-source:**
-i[regexp] - filter out from the list of files for the diff
-i by itself enables the option, with a default regexp that will filter out control files and directories  of  the  most  common revision control systems, backup and swap files and   Libtool build output directories. 

-I[file-pattern]
              If  this  option  is  specified,  the  pattern will be passed to tar(1)'s --exclude option  when  it  is  called  to  generate  a .orig.tar  or  .tar  file. 

              -I by itself adds default --exclude options that will filter out control  files  and directories of the most common revision control systems, backup and swap files  and  Libtool  build  output directories.

---

### Post by knipknap on 2010-01-23
Thank You, the "-I" switch did it!

---

