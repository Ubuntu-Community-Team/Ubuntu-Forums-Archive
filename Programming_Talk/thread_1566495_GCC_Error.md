---
title: "GCC Error"
date: 2010-09-02
forum: Programming Talk
---

### Post by Mr.Macdonald on 2010-09-02
Why do I get the below error?

[Code]("http://pastebin.com/rw2zQkHk")


> $ gcc main.c -o main
main.c:22:22: error: expected ';', ',' or ')' before '&' toke

---

### Post by Zugzwang on 2010-09-02
That's because you are trying to define that the second function takes a reference to a pointer to a pattern as its first argument. References do however not exist in C, only in C++. Compile with g++ if you really want a reference to a pointer.

---

### Post by Krupski on 2010-09-02
> **Mr.Macdonald said:**
> Why do I get the below error?

[Code]("http://pastebin.com/rw2zQkHk")

Maybe because the code is gibberish?

What is it supposed to do? There's no functioning code visible. Did you provide the proper link?

---

### Post by Mr.Macdonald on 2010-09-02
The code doesn't have to do anything to get that error.

No references! At least we got pointers

---

### Post by Zugzwang on 2010-09-03
> **Mr.Macdonald said:**
> No references! At least we got pointers

Erm, what is this supposed to mean?

---

