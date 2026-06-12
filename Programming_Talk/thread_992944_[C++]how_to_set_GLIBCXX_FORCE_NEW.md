---
title: "[C++]how to set GLIBCXX_FORCE_NEW?"
date: 2008-11-25
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-11-25
I have a C++ program where I use many functions of std::string and std::vector. I am using valgrind and I am getting some "leaks" related to these functions. But as I read here-->[http://valgrind.org/docs/manual/faq.html#faq.reports](http://valgrind.org/docs/manual/faq.html#faq.reports)
I need to set the GLIBCXX_FORCE_NEW env variable to immediately free the memory from the pool.
Can you give me an example on how to do this? I don't have clue...

---

### Post by Trail on 2008-11-25
Edit: type "export GLIBCXX_FORCE_NEW" in the same terminal where you are running your program.

---

### Post by SledgeHammer_999 on 2008-11-25
thank you

---

