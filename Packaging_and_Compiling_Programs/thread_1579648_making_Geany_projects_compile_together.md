---
title: "making Geany projects compile together"
date: 2010-09-22
forum: Packaging and Compiling Programs
---

### Post by scalyanteater on 2010-09-22
I am using Geany as the IDE for C++ on Ubuntu 9.10. I have defined a project, containing 

[LIST]
[*]application.cpp
[*]header.h
[*]main.cpp
[/LIST]
main.cpp has an "include" line for the header and application.cpp, and it works fine. However, people say that I should be able to run main.cpp as part of the project *without* including application.cpp , and because they are part of the same project the compiler will know to include application.cpp at the right time.

But I can't get that to work. Are there settings I should be using to make this happen?

Thanks!

---

