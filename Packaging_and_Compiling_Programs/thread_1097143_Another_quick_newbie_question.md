---
title: "Another quick newbie question"
date: 2009-03-15
forum: Packaging and Compiling Programs
---

### Post by 10Zav01 on 2009-03-15
root@BlackMagicBox:/# g++ -o practice practice.cpp
root@BlackMagicBox:/# practice
bash: practice: command not found

// Listing 2.2 using std::cout
#include <iostream>
int main()
{
    std::cout << "Hello there.\n";
    std::cout << "Here is 5: " << 5 << "\n";
    std::cout << "The manipulator std::endl ";
    std::cout << "writes a new to the screen.";
    std::cout <<  std::endl;
    std::cout << "Here is a very big number:\t" << 70000;
    std::cout << std::endl;
    std::cout << "Here is the sum of 8 and 5:\t";
    std::cout << 8+5 << std::endl;
    std::cout << (float) 5/8 << std::endl;
    std::cout << "And a very very big number:\t";
    std::cout << (double) 7000 * 7000 << std::endl;
    std::cout << "Don't forget to replace Jessie Liberty";
    std::cout << "with your name...\n";
    std::cout << "Paul is a C++ programmer!\n";
    return 0;
}


okay the Hello World one worked just dandy. this one compiled right but it didn't run when i typed in it's name, is there something I am doing wrong?

---

### Post by snova on 2009-03-15
> **10Zav01 said:**
> root@BlackMagicBox:/# g++ -o practice practice.cpp
root@BlackMagicBox:/# practice
bash: practice: command not found

That should be

```
./practice
```

Because Bash does not search the current directory for executables.

Also, why are you running as root? And putting files in /?

---

### Post by 10Zav01 on 2009-03-15
just easy to do, didn't use command lines for a long time so I decided to practice it some.

---

