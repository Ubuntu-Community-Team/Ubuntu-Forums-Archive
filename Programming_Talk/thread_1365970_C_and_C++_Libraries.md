---
title: "C and C++ Libraries"
date: 2009-12-27
forum: Programming Talk
---

### Post by shaaaadoooow on 2009-12-27
Does anyone have a shell script that installs needed libraries for C and C++? (e.g. Boost libraries, Xalan libraries, etc.) Thanks for the help. :)

---

### Post by Bachstelze on 2009-12-27
You will find all those libraries in your favourite package manager.

---

### Post by jpeddicord on 2009-12-27
[build-essential]("apt:build-essential") is likely what you want.

---

### Post by shaaaadoooow on 2009-12-27
Thanks for the replies. :)

---

### Post by Bachstelze on 2009-12-28
> **jpeddicord said:**
> [build-essential]("apt:build-essential") is likely what you want.

Nope. It only includes the core libraries, not additional libraries like Boost or Xalan.

---

### Post by jpeddicord on 2009-12-28
> **Bachstelze said:**
> Nope. It only includes the core libraries, not additional libraries like Boost or Xalan.

good point. libboost1.38-dev and libxalan110-dev in addition, then. :)

---

