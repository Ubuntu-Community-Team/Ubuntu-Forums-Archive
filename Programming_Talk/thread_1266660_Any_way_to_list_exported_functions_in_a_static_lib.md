---
title: "Any way to list exported functions in a static library?"
date: 2009-09-14
forum: Programming Talk
---

### Post by misha680 on 2009-09-14
I tried grep but it gives me both exported functions and dependencies...

Thank you
Misha

---

### Post by slavik on 2009-09-14
look at the header file?

---

### Post by dribeas on 2009-09-15
nm should help you there. I don't have a linux box right now, but calling:

nm library.a [--demangle]

should list all the internal object files with the symbols they define.

---

### Post by misha680 on 2009-09-15
> **dribeas said:**
> nm should help you there. I don't have a linux box right now, but calling:

nm library.a [--demangle]

should list all the internal object files with the symbols they define.

Thank you. Is there any way to just get exports? I think the exports are
in uppercase but for some reason I'm still getting undefined symbol errors linking with that library.

Thank you
Misha

---

### Post by dribeas on 2009-09-15
I don't think there is such thing as an exported function (as compared to a non-exported function). Static libraries in linux are just a bunch of object files packed together into a single file. I don't quite understand what you mean by 'exports are in uppercase', exported symbols will be just as the code defines them, neither the compiler nor the linker will change the symbol names for any reason.

Also note that gcc does not require you to add an export declaration to the symbols you want publicized in a library. All symbols are exported when compiled with gcc.

---

