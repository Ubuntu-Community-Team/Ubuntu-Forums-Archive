---
title: "More Compiling Trouble"
date: 2005-04-12
forum: Packaging and Compiling Programs
---

### Post by ZetSabre on 2005-04-12
While trying to compile a program, I keep getting this error:

warning: #warning This fi le includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples in clude substituting the <X> header for the <X.h> header for C++ includes, or <sst ream> instead of the deprecated header <strstream.h>. To disable this warning us e -Wno-deprecated.

I tried some searches and couldn't find anything specific to what I'm doing. Any ideas? (if it isn't already obvious, i'm incredibly new to programming).

---

### Post by jerome bettis on 2005-04-12
well if it's just a warning don't worry about it.

if that's all it says, it finished compiling, and your object file is there.  unless you got an **error**.

---

### Post by ZetSabre on 2005-04-12
Hmm; then it's either not creating a new file, or I can't find it. I assumed it would be a.out.

Does anyone know what I should do?

---

