---
title: "What's static variable/function outside a function (in C)?"
date: 2008-11-29
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-29
Title explains everything.

---

### Post by winch on 2008-11-29
It's used to limit the scope of a global to the file it's declared in.

Google for "c storage classes" for more info.

---

### Post by nvteighen on 2008-11-29
Welcome to the sole ambiguity in C. 'static' has two differents meanings depending on whether is applied to a variable or to a function.

**static variable** It's a persistent variable local to where it has been declared (if declared at toplevel, it's global). By persistent, I mean that its value is preserved, not lost after the function returns (why? because a static variable is not stored into the stack).

**static function** A private function only accessable within the module it was declared. For example, this is very handy when you develop a library and need to write a function that implements stuff for internal workings and not for outside use... by declaring that function as static, you exclude it from your library's API/ABI (actually this is not true, as you could access it using Assembly).

---

