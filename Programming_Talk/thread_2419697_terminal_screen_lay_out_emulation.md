---
title: "terminal screen lay out emulation"
date: 2019-05-25
forum: Programming Talk
---

### Post by Skaperen on 2019-05-25
i don't want to re-invent this wheel.  i need a subset of terminal emulation where a stream of characters is formatted into a screen area.  at periodic times i will need to fetch the contents of the screen as a 2-dimensional array.  i also need to be able to set the screen size (such as 80x25 but usually much larger) once at the start.  it needs to able to emulate some terminal type.

there will be basically four operations i need to do:
```
1. create a new screen instance and if successful be returned a pointer or reference to it.
2. pass to it part of the character stream, a variable amount.  this will be the most frequent operation and may be just one character at a time quite often.
3. requests for the screen contents.  it may do one of many ways and i can code to this.
    a. returns a pointer or reference to the live array it formats on, or a copy ofit.
    b. allocates memory and makes a copy in that memory for the caller to use and free.
    c. the caller passes a pointer or reference to an appropriate sized buffer for a copy of the screen to be written to.
4. a destruct operation when finished.
```

a version that can support Unicode via UTF-8 coming in on the stream would be a big plus. the returned/yielded screen array would have a character type that can handle the wide range of Unicode characters with their overlaying modifiers in formatting. but, at the very minimum i need full ASCII, support a controls its terminal type support.  the preferred type is the one emulated by the Linux kernel for VTs.

i suppose it might be possible to use the kernel to emulate this by feeding the virtual terminals and reading their screen contents back

using the screen program is not an option.  i am using it now and there are issues i am trying to get away from.

i prefer something i can use by coding in Python, but i can do C just fine.

does anyone know of a library, module, program, or source collection that can do this, without the hassle of ripping out selections of code from some full terminal emulator?

---

