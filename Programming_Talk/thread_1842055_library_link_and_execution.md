---
title: "library link and execution"
date: 2011-09-10
forum: Programming Talk
---

### Post by luishasbon on 2011-09-10
Dear comunity, greetings.

I made this app using opencv 2.3.0, the thing is that after the compiling process using eclipse, everything resulted without issues, when i executed the program it threw an exception regarding the libopencv_core2.3.0, this lib couldnt be found, I fix this by updating the ldconfig set, but the question is, despite compiled the program do I still need to use the library for it to work, what i mean is, in an other person pc without the library, it wont work?

Thanks

---

### Post by Senesence on 2011-09-10
> **luishasbon said:**
> Dear comunity, greetings.

I made this app using opencv 2.3.0, the thing is that after the compiling process using eclipse, everything resulted without issues, when i executed the program it threw an exception regarding the libopencv_core2.3.0, this lib couldnt be found, I fix this by updating the ldconfig set, but the question is, despite compiled the program do I still need to use the library for it to work, what i mean is, in an other person pc without the library, it wont work?

Thanks

Well, obviously, if the program throws an exception indicating that it can't find libopencv_core2.3.0, then that would indicate that this library is required, on your, or any other computer.

---

