---
title: "Standards and backward compatibility"
date: 2009-02-15
forum: Programming Talk
---

### Post by ajackson on 2009-02-15
Here is an interesting one for discussion.

When standards change, do they necessarily have to be backwards compatible? Are there situations where it is OK for backwards compatibility to break or should a developer expect code that compiled and ran with one version to compile and run **without any alteration** in the next version or, say, 5 versions down the line?

IMHO breaking backwards compatibility should be avoided where possible but sometimes it has to be done to advance the language (i.e. a badly implemented function/class needs a re-write but the various parameters, etc need to change to fit the new implementation).

Newer languages I guess are more prone to this as they are still relatively early on in their overall life time. But even older languages could fall foul if particular implementations have been plugging a hole in the standards but now that hole is getting filled with a standard version of that class/function (as I doubt they'd keep the existing implementation and the new standard implementation).

Any opinions on this?

---

### Post by PythonPower on 2009-02-15
I guess a good case example would be OpenGL 3.0 - although that actually looks backwards compatible in the end. However, major changes were proposed to change the standard from a procedural API to a more object-orientated one.

I don't think there is any requirement in the definition of a "standard" for backwards compatibility. All the same, it is desirable in most cases.

---

