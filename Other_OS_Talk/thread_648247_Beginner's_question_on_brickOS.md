---
title: "Beginner's question on brickOS"
date: 2007-12-23
forum: Other OS Talk
---

### Post by Suraine on 2007-12-23
dear brickOS guru:

im new in brickOS. i had installed a 5.0.3.32 version of brickOS.
im trying to declare the "main()" function with "void",

however, when compiling, it requires me to changed the type to "int", and they is a bug saying:

" '0' is cannot be used as a function."

why is that so?

thanks,
suraine

---

### Post by PriceChild on 2007-12-23
*moves to Other OS talk*

---

### Post by saulgoode on 2007-12-23
The 'main()' function is defined by ANSI C as returning a value of type 'int' -- no allowance is made for a 'void' return. Even though ANSI made the wrong choice, it is probably best to follow that convention. Depending upon the compiler you are using, the compiler can be instructed to ignore the error with the '-Wno-main' switch.

---

### Post by Suraine on 2007-12-23
Thanks for the information, saulgoode.

Since im not familiar with system stuff, therefore im not really know what is a compiler is. is it the makefile?

U mention:
"Depending upon the compiler you are using, the compiler can be instructed to ignore the error with the '-Wno-main' switch."

How can i achieve that?

Thanks again :)

---

