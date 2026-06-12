---
title: "How To Build a Kernel PPA"
date: 2011-02-05
forum: Packaging and Compiling Programs
---

### Post by nutznboltz on 2011-02-05
Building a kernel PPA is a bit more tricky than other PPAs and it's not documented anyplace that I can find via google today.

The first landmine is that the debian.master/changelog gets automatically copied to debian/changelog but too late in the build process to rely on it being done on time.  Copy the changelog into both locations before using debuild.

Next you will find that the make options aren't going to work, you will crash into errors about abi files.  In debian.master/rules.d/i386.mk and debian.master/rules.d/amd64.mk you will need to add these lines:

```

skipabi         = true
skipmodule      = true
skipdbg         = true
no_dumpfile     = true
do_doc_package  = false
do_source_package       = false
do_full_source          = true
do_common_headers_indep = true
do_libc_dev_package     = false
do_tools                = false
```

---

