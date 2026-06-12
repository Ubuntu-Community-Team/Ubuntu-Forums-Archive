---
title: "Error in compiling firefox, missing iwlib.h"
date: 2009-08-08
forum: Packaging and Compiling Programs
---

### Post by carfield on 2009-08-08
Get the following message:

```
configure: error: Can't find header iwlib.h for Necko WiFi scanning (might be in package libiw-dev (Ubuntu) or wireless-tools-devel (Fedora)); use --disable-necko-wifi to disable

```

However, I've installed libiw-dev already. As I try to compile 32bit firefox in 64bit system, I've also double checked there is no lib32iw-dev. Anyone know why I still get this error?

---

### Post by lovinglinux on 2009-08-09
I'm getting the same error while compiling FF 3.6a1

Not related to this error, but I'm also getting some errors while compiling FF 3.5.2.

EDIT:

use the option below to avoid this error:

```
ac_add_options --disable-necko-wifi
```

---

### Post by carfield on 2009-08-09
> **lovinglinux said:**
> I'm getting the same error while compiling FF 3.6a1

Not related to this error, but I'm also getting some errors while compiling FF 3.5.2.

EDIT:

use the option below to avoid this error:

```
ac_add_options --disable-necko-wifi
```
Yes, finally I do that also. However I need to edit ~/browser/config/mozconfig instead of ~/mozconfig make it this work.

---

### Post by lovinglinux on 2009-08-09
> **carfield said:**
> Yes, finally I do that also. However I need to edit ~/browser/config/mozconfig instead of ~/mozconfig make it this work.

Put mozconfig inside the source folder and it should work.

I'm testing 3.6a1 right now and I'm impressed.

---

