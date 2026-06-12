---
title: "Terminal C++ Can't Find STL"
date: 2009-08-16
forum: Programming Talk
---

### Post by socool274 on 2009-08-16
I'm new to Ubuntu, this is the 3rd day of Ubuntu use. I am a C++ game programmer, and would liked to have compiled a C++ program. Unfortunately, when I used g++ in the terminal for compiling, anything in the STL (strings, vectors, fstreams) wouldn't be found. I included them properly: <string>, <vector>, <fstream>. Yet, whenever I tried to make an instance of any of these, it would say that it is not a type. Does anybody know why this is happening? If so, how it can be fixed? :confused: Ask me for more information when you need it.

---

### Post by pepperphd on 2009-08-16
Do you have "using namespace std" or "using std::whatever" in your source?

---

### Post by JordyD on 2009-08-16
Could you show some example code?

---

### Post by socool274 on 2009-08-16
Oh, I'm sorry, I had forgotten that for the STL, you needed std. That was a stupid mistake, thanks pepperphd. Thanks for the help, I got it.

---

