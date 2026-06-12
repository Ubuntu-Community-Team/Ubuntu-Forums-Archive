---
title: "Code::Blocks"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by FaBioW114 on 2008-09-05
Hi,

I've been trying to install code::blocks via terminal, but didn't get to do it. I'm using Ubuntu 7.04 (Feisty Fawn) and I've searched for some tutorials, and almost everything went okay, except the the final step, when this message appears:

The following packages have unmet dependencies:
  wx-common: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
             Depends: libgcc1 (>= 1:4.2.1) but 1:4.1.2-0ubuntu4 is to be installed
             Depends: libstdc++6 (>= 4.2.1) but 4.1.2-0ubuntu4 is to be installed
             Depends: libwxbase2.8-0 (>= 2.8.8.1) but it is not going to be installed
             Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
E: Broken packages

I have no idea of what that is... Please help!

---

### Post by StOoZ on 2008-09-05
just download the ubuntu version from here:
[http://www.codeblocks.org/downloads/5]("http://www.codeblocks.org/downloads/5")


If you are planning on writing wxWidgets projects , install wxWidgets first.

---

### Post by FaBioW114 on 2008-09-05
yeah, I've tried that too, but when I run each of the extracted files, an error message appears. For example, when I double click the libwxsmithlib0 package, this comes up: "Error: Dependency is not satisfiable: libcodeblocks0"

and below that, there is:

wxSmith shared library (wxSmith is a Code::Blocks plugin for RAD GUI editing)
This package contains the wxSmith shared library.
[http://www.codeblocks.org](http://www.codeblocks.org) 

The other packages show different error messages and none of them is installable.

---

### Post by StOoZ on 2008-09-06
ok , first of all , installed the latest version of wxwidgets , you'll need to compile it etc.
after that , install from the link that I provided , Code::blocks , thats exactly how I did it and it works.

---

