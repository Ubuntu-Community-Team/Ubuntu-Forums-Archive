---
title: "Cmake defines"
date: 2009-05-12
forum: Programming Talk
---

### Post by kerryhall on 2009-05-12
I have a quick question about cmake. I have searched for days, but cannot seem to find the answer to this question.

I want to be able to provide a define some of the time. For example, I want to be able to do -DDEBUG some of the time. I know the add_definition() macro, but I don't want to have to edit my CMakeLists.txt every time I want to change a define.

Thanks!

---

### Post by kerryhall on 2009-05-25
Bump.

---

### Post by mart_k on 2009-05-25
> **kerryhall said:**
> I have a quick question about cmake. I have searched for days, but cannot seem to find the answer to this question.

I want to be able to provide a define some of the time. For example, I want to be able to do -DDEBUG some of the time. I know the add_definition() macro, but I don't want to have to edit my CMakeLists.txt every time I want to change a define.

Thanks!You first define a [option](http://www.cmake.org/cmake/help/cmake2.6docs.html#command:option). This means that you can change that option in ccmake. After that you add a IF-statement to see how the option is set. Depending on the value of that option, you execute add_definition or not.

---

### Post by kerryhall on 2009-06-04
Thanks! Very helpful! :)

---

