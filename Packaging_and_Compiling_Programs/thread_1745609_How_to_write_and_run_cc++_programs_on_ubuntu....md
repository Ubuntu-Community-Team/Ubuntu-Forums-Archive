---
title: "How to write and run c/c++ programs on ubuntu..."
date: 2011-05-01
forum: Packaging and Compiling Programs
---

### Post by dilipkumarthota on 2011-05-01
Hii  Uforum,
                can any one tel me how to write and execute c/c++ code on ubuntu.. and please do specify the software to be dowloaded...
thanking you,,:P

---

### Post by tb13 on 2011-05-02
Sure thing,

1) First of all you are going to want to download and install the C and C++ compilers. For this you need to enter this code into the terminal:
[B]
sudo aptitude install build-essential[/B]

2) For C Programming to write your c program enter the following:

**sudo gedit first.c**

then enter this:

[B]#include <stdio.h>

int main()
{
printf("Hello World\n");
return 0
}[/B]

3) Next you need to compile your C Code that you have just entered. To do this type in the following command:

[B]cc -c first.c

[/B]This will create an object file, to create an executable file type in:

[B]cc -o first.c

[/B]4) To run the program finally type:
[B]
./first
[/B]

---

### Post by tb13 on 2011-05-02
Also, for C++,

[B]sudo gedit first.cpp

#include <iostream>

int main()
{
cout << "Hello World!" << endl;
return 0;
}

[/B]Then a slight difference in the compiling type:

[B]g++ first.cpp -o programname

[/B]then:

**./programname**

---

### Post by ApOgEEs on 2011-05-27
My step by step instructions.

1. Install the 'build-essential' package.
```
$ sudo apt-get install build-essential
```

2. Write your first C program. 
```
gedit myhello.c
```
  paste this code into it, and save
```

#include <stdio.h>

main()
{
   printf("Hello Ubuntu Lover!\n");
}

```

3. Compile your first C program
```

$ gcc myhello.c -o myhello

```

4. Run your first C program
```

$ ./myhello 
Hello Ubuntu Lover!

```

5. Write your first C++ program
```
gedit myhello.cpp
```
  paste this code into it, and save
```
#include <iostream>
using namespace std;

int main()
{
   cout << "Hello Ubuntu Lover in C++" << endl;
   return 0;
}
```

6. Compile your first C++ program
```
g++ myhello.cpp -o myhellocpp
```

7. Run your first C++ program
```
$ ./myhellocpp 
Hello Ubuntu Lover in C++

```

Good Luck!

---

### Post by rpmp on 2011-05-27
look for C/C++ tutorials to learn to write programs and to compile use CODEblocks ide then when you finish writing the program (in code blocks) hit Build then Build and run and with that you compile it and executed it.

---

### Post by Petrolea on 2011-05-28
> **tb13 said:**
> Also, for C++,

[B]sudo gedit first.cpp

#include <iostream>

int main()
{
cout << "Hello World!" << endl;
return 0;
}

[/B]Then a slight difference in the compiling type:

[B]g++ first.cpp -o programname

[/B]then:

**./programname**

Why would you want to run gedit with 'sudo'? And even if you would have to, it's still recomended to run it with gksu.

---

