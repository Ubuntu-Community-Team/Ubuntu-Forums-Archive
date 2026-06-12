---
title: "Advantages using int32 instead of int?"
date: 2008-05-19
forum: Programming Talk
---

### Post by paukku92 on 2008-05-19
Is there any advantages of using int32 instead of int in variable declarations when using C/C++?

---

### Post by LaRoza on 2008-05-19
> **paukku92 said:**
> Is there any advantages of using int32 instead of int in variable declarations when using C/C++?

They don't exist. I think it may be an MS thing though, but that isn't C or C++.

[http://www.space.unibe.ch/comp_doc/c_manual/C/CONCEPT/data_types.html](http://www.space.unibe.ch/comp_doc/c_manual/C/CONCEPT/data_types.html)

---

### Post by paukku92 on 2008-05-19
Well, seeing int32 in SDL examples made me wondering. Thank you for the answer.

---

### Post by dasunst3r on 2008-05-19
Something tells me that it has to do with how big of a number the variable can hold.  I think this should give you a bit more insight on this: [http://en.wikipedia.org/wiki/Integer_(computer_science](http://en.wikipedia.org/wiki/Integer_(computer_science))

---

### Post by LaRoza on 2008-05-19
> **paukku92 said:**
> Well, seeing int32 in SDL examples made me wondering. Thank you for the answer.

It may be a typedef somewhere. It isn't a native datatype. It may SDL's way of having a 32 bit integer regardless of the platform. (The size of an "int" and "long int" are not always different)

---

### Post by utUtu on 2008-05-19
> **paukku92 said:**
> Is there any advantages of using int32 instead of int in variable declarations when using C/C++?

It depends on what is your default int variable is.  It could have been defined as 16-bit or 64-bit depending on your env.  Obviously, int32 is a 32-bit variable.  So if say you have int is a 16-bit, and you need an integer much larger than 32,767, then you need a 32-bit variable.  Hence you need the int32.

---

### Post by samjh on 2008-05-19
The C99 standard includes data type names like int32_t, int64_t, etc.  Obviously int32_t is a 32-bit signed integer, int64_t is 64-bit, etc.

Take a look at your /usr/include/stdint.h file.

The only advantage is if you need assurance that your integer will be no more or less than a specific size.

---

