---
title: "Qt Creator and C"
date: 2010-11-20
forum: Programming Talk
---

### Post by heatblazer on 2010-11-20
Hello, recently I have installed qt creator last stable on my ubuntu 8.04. I tested to compile a simple io program but it gives me an error. The same build runs on my qemu-kvm WinXP - Visual C++ Express 2010 but not on the qt creator... any info? I am attaching screenshot.

---

### Post by GregBrannon on 2010-11-20
Your cpp program is not in the typical c++ format:

```

// my first program in C++

#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}

```

Revise yours to follow the above model, and it'll be fine.

---

### Post by heatblazer on 2010-11-20
It worked, I just removed the void main() to just main()... And add an option to run n therminal... Everything seems ok now.

---

### Post by nvteighen on 2010-11-20
No, not "main()", but "int main()"... The C++ standard requires main to return an integer and GNU/Linux (and UNIX/Unix-like OSs in general) uses that returned integer as a mean to know whether the application ended succesfully or not (0 = success... something else = error). Although the C++ standard allows not writing an explicit return statement for main, the return type has to be correct.

Ok, yes, your application works anyway, regardless of what I've said above. But that's because g++ has done the job; other compilers may not support that outdated non-standard style.

---

