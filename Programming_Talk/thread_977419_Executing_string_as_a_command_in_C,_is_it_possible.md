---
title: "Executing string as a command in C, is it possible, and if so, how to do it?"
date: 2008-11-10
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-10
In python, **exec** does this thing. But is there any equivalent in C for it?

I'm suspecting it is impossible, as C isn't interpreted language. :(

---

### Post by Sinkingships7 on 2008-11-10
I think you're looking for the system() function. It takes a string as an arg, like this:
[php]
system("cp /data/files /other/location");
[/php]
You'll need the stdlib.h header for this function.

---

### Post by Cracauer on 2008-11-10
dlopen(3)

---

### Post by CptPicard on 2008-11-10
No, there is no "eval" function (in lisp terms) in C -- runtime evaluation of code -- for exactly the reason you suspect.

---

### Post by crazyfuturamanoob on 2008-11-10
@Sinkingships7:
I don't want to run a command in terminal. I want to execute the string as C code, like:
```
executemystring("int a = 5;");
printf("%i", a);
```

---

### Post by crazyfuturamanoob on 2008-11-10
> **CptPicard said:**
> No, there is no "eval" function (in lisp terms) in C -- runtime evaluation of code -- for exactly the reason you suspect.

Perhaps I could then embed Python or Lua or any other interpreted language within my program?

---

### Post by CptPicard on 2008-11-10
> **crazyfuturamanoob said:**
> Perhaps I could then embed Python or Lua or any other interpreted language within my program?

Yep, that's the ticket.

---

### Post by Cracauer on 2008-11-10
> **crazyfuturamanoob said:**
> @Sinkingships7:
I don't want to run a command in terminal. I want to execute the string as C code, like:
```
executemystring("int a = 5;");
printf("%i", a);
```

As I said, dlopen(3) is your only option.

Write C, compile it to an object file, load it, call the function inside.

---

