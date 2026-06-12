---
title: "C++ iostream"
date: 2009-12-19
forum: Programming Talk
---

### Post by NTHQ on 2009-12-19
I hadn't done C++ in a few years so I decided to take out my old book that I learned from to refresh myself. Back then I used Visual C++ to write my programs. When I started programming in Java I used Eclipse and got used to it. So I installed it in Ubuntu and also got CDT to do my C++ programming.
I'm having trouble with these two programs that came from my book.
```
#include <iostream>
using namespace std;
int main()
{
    int ch;
    int count = 0;
    while((ch = cin.get()) != EOF)
    {
        cout << char(ch);
        count++;
    }
    cout << "\nCharacter count = " << count << "\n";
    return 0;
}

``````
#include <iostream>
using namespace std;
const int Size = 10;
int main()
{
    int grades[Size];
    cout << "\nEnter student grades.";
    cout << "\nProgram terminates beyond " << Size << " entries ";
    cout << "or a -ve entry\n";
    int num;
    cin >> num;
    int i = 0;
    while(i < Size && num >= 0)
    {
        grades[i++] = num;
        if(i < Size)
            cin >> num;
    }
    if(i == 0)
        cout << "\nNo grades entered!\n";
    else
    {
        fflush(stdin);
        cout << "\nEnter your grade: ";
        int grade;
        cin >> grade;
        int count = 0;
        for(int j = 0;j < i;j++)
            if(grades[j] > grade)
                count++;
        cout << count << " students have a higher grade than you\n";
    }
    return 0;
}

```This is what the console gives when I try to build each program respectively.
```

**** Build of configuration Debug for project PROG30 ****

make all 
Building file: ../prog30.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"prog30.d" -MT"prog30.d" -o"prog30.o" "../prog30.cpp"
../prog30.cpp: In function ‘int main()’:
../prog30.cpp:7: error: ‘EOF’ was not declared in this scope
make: *** [prog30.o] Error 1

``````

**** Build of configuration Debug for project PROG33 ****

make all 
Building file: ../prog33.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"prog33.d" -MT"prog33.d" -o"prog33.o" "../prog33.cpp"
../prog33.cpp: In function ‘int main()’:
../prog33.cpp:23: error: ‘stdin’ was not declared in this scope
../prog33.cpp:23: error: ‘fflush’ was not declared in this scope
make: *** [prog33.o] Error 1

```From what I know, EOF, stdin, and fflush should all be declared inside iostream no? So why does it tell me that they are not?

---

### Post by unknownPoster on 2009-12-19
I compiled your first program manually via:
```
g++ -Wall file.cpp -o run
```

Everything compiled and ran successfully that way. 

I believe there may be an issue with your build configurations. I only use Eclipse for Java development so I'm not exactly sure how to assist you with Eclipse and C++.

---

### Post by Brandon Williams on 2009-12-19
EOF, stdin, and fflush are all part of the C stdio library. You may need to include <cstdio> to get those. It's generally better to avoid mixing iostream and stdio, though. Just use functionality that's in iostream instead. Look [here](http://www.cplusplus.com/reference/iostream/istream/get/) for an alternate example of how to use istream::get for character based input. And just use cin.flush() to flush stdin.

---

### Post by NTHQ on 2009-12-19
This is what I wrote in my makefile.
```
all:
g++ prog30.cpp -o prog30

```I am not very familiar with makefiles since I didn't have to write them in Visual C++. Could there be something wrong there?

---

### Post by NTHQ on 2009-12-19
> **Brandon Williams said:**
> EOF, stdin, and fflush are all part of the C stdio library. You may need to include <cstdio> to get those. It's generally better to avoid mixing iostream and stdio, though. Just use functionality that's in iostream instead. Look [here]("http://www.cplusplus.com/reference/iostream/istream/get/") for an alternate example of how to use istream::get for character based input. And just use cin.flush() to flush stdin.
I included cstdio and and it works now thanks a lot. :)

---

### Post by dwhitney67 on 2009-12-19
EOF is indeed a C thingy.

In C++, the while-conditional should be something similar to:
```

while((ch = cin.get()) && !cin.eof())
{
   ...
}

```


P.S.  It should be noted that this also would have worked:
```

char ch;
int count = 0;
while(cin.get(ch))
{
   ...
}

```

---

