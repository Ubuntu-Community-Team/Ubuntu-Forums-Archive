---
title: "SOS PYTHON createprocess"
date: 2010-01-26
forum: Programming Talk
---

### Post by capitalfear on 2010-01-26
okay so I'm trying to make this python code, right?

from ctypes.wintypes import BOOL, LPCSTR
BOOL WINAPI CreateProcessA(
LPCSTR lpApplicationName,)

and it goes on much longer than that but you get the point...So what I did was 
BOOL WINAPI CreateProcessA(

but it said BOOL wasn't defined...even though it was later in the code...anyways how Do i get WINAPI to be a "defined variable"

---

### Post by cariboo on 2010-01-26
A bump for the move.

---

### Post by lukeiamyourfather on 2010-01-26
What's wrong with subprocess.Popen?

---

