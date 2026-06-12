---
title: "CLI mime entry"
date: 2005-08-03
forum: Programming Talk
---

### Post by m87 on 2005-08-03
```
marco@pride:~/Programmi/MONO$ file anything.exe
anything.exe: MS Windows PE 32-bit Intel 80386 console executable
```

i don't like CLI executables being recognised as "win32 executables", maybe because it's COMMON language interface, maybe because i'm on a 64bit box.

does anyone know IF both win32 and CLI binaries actually share the same mimetype? is there any way to change this? if we want to think of mono as an open implementation of an iso/ecma standard, we should avoid some names, afaiac.

marco

---

### Post by LordHunter317 on 2005-08-04
[QUOTE=m87]i don't like CLI executables being recognised as "win32 executables",[/quote]Well, that's what they are.

file(1) simply is looking at the header of the executable file.  And CIL binaries use Microsoft's Portable Executable (PE) format.  It isn't smart enough to know the difference.

> does anyone know IF both win32 and CLI binaries actually share the same mimetype?I don't know, but that's not what file is looking at.  They certainly share the same executable file format, that's for sure.

>  is there any way to change this?Nope.

>  if we want to think of mono as an open implementation of an iso/ecma standard, we should avoid some names, afaiac.Can't, part of the standard.   You could change what file prints, but that would be simply silly, IMO.

---

### Post by m87 on 2005-08-04
yup, that's what I meant.

I didn't know if they share the same header. if they do, this sucks a bit, maybe because CLI is NOT windows...

---

