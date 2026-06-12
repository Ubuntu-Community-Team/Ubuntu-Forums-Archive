---
title: "Eclipse code completion works partily"
date: 2008-11-09
forum: Programming Talk
---

### Post by caonima on 2008-11-09
I use Eclipse 3.2.2 on Ubuntu 8.04 for C++ programming. The code completion function only works for classes defined in user headers but not library headers. For example, I have
#include <fstream>
#include <iostream>
using namespace std;

int main(){
   ifstream ifs;
return 0;
}

"ifs." gives a blank box without any hints. The program compiles and the headers are found. So what could be the problem?

---

### Post by dribeas on 2008-11-09
> **caonima said:**
> I use Eclipse 3.2.2 on Ubuntu 8.04 for C++ programming.

Eclipse CDT has evolved quite a bit. I would suggest downloading the latest version (CDT 5) as there has been many improvements (or so they say) I tried CDT 3 had problems interpreting templated code (finding usage of a method, finding the template code for a call on a template argument) that might be your case now (ifstream is a template with default arguments).

---

### Post by caonima on 2008-11-09
> **dribeas said:**
> Eclipse CDT has evolved quite a bit. I would suggest downloading the latest version (CDT 5) as there has been many improvements (or so they say) I tried CDT 3 had problems interpreting templated code (finding usage of a method, finding the template code for a call on a template argument) that might be your case now (ifstream is a template with default arguments).

Just tried the latest CDT. Same problem.

---

