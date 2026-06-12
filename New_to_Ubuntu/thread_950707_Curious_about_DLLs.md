---
title: "Curious about DLLs"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by donom on 2008-10-17
From what I vaguely gather, DLLs are used by Windows to communicate with devices on a lower level. If that's even correct, what's the equivalent of it in Linux? Does it handle it too differently to even have an equivalent?

---

### Post by DrMega on 2008-10-17
> **donom said:**
> From what I vaguely gather, DLLs are used by Windows to communicate with devices on a lower level. If that's even correct, what's the equivalent of it in Linux? Does it handle it too differently to even have an equivalent?

DLLs in Windows are just libraries to do all sorts of things, not necessarily low level. A DLL is just a Dynamic Linked Library, meaning that it is linked to the program that needs it at run time as opposed to at compile time.

Linux has an equivalent, but they just don't get called DLLs (and don't have the DLL extension). They are used in much the same way, to provide common functionality without each program having to implement it individually.

An example (in summary) would be the scenario in Windows, where each Windows app doesn't have to worry about how to draw a window, or how to draw command buttons, the program just uses library functions to do that. Linux does the same, except that there are more choices of library to do specific things.

---

