---
title: "[SOLVED] C++: array length... low level, vector?"
date: 2008-10-15
forum: Programming Talk
---

### Post by ChrisBookwood on 2008-10-15
Hi,

I working on an app that takes different arguments (int argc, char *argv[]). The problem I'm having, is getting the length of argv - number of items/arguments in it. I' have tried doing both these things, but either return 4, even though i'm only passing 2 (including argv[0]) or 3 arguments.

int i = ( sizeof( argv ) / sizeof ( char )); // 4

and,

vector <char> arl;
arl.push_back ( argv );
int i = arl.size(); // 4

Where am I going wrong?

---

### Post by WW on 2008-10-15
Why don't you just use argc?  That's exactly what it is.

---

### Post by ChrisBookwood on 2008-10-15
Omg, why haven't i thought of that! Embarrasing, it is.
Thanks:P

But I would still like to know why my methods doesn't work?

---

### Post by hod139 on 2008-10-15
argv is a pointer to a char array.  Pointers on your machine must be 4 bytes (32 bits).  Even if you asked for the size of argv[n], you would still get 4, since argv[n] is a pointer to where in memory the char array starts, and again pointers are 4 bytes on your machine.

---

### Post by ChrisBookwood on 2008-10-15
Ahh, yeah, but what confused me, and still does, is that &argv doesn't work either, which actually was my main try out, but since it had the same result as without the ambersand, I've let it slip my mind.

---

### Post by dribeas on 2008-10-15
On the use of sizeof (C++, don't know if this is precise in C)

When applied to a type will give you the space requirements of the data type.
```

std::cout << sizeof(int); // 4 with 32 bit integers
std::cout << sizeof(char); // 1
std::cout << sizeof(int*); // 4 in x32 architectures, 8 in x64

```

When applied to a variable it will give you the size that the variable takes in memory, which for arrays it is the size of the data type times the number of elements:
```

int a;
int ar[100];
int *ap = new int[100];

std::cout << sizeof(a); // 4, same as sizeof(int)
std::cout << sizeof(ar); // 400, 100 x sizeof(int)
std::cout << sizeof(ap); // 4 / 8, same as sizeof(int*)
std::cout << sizeof(*ap); // 4, same as sizeof(int) as *ap is just the first int

```

In the case of the pointer, the variable is not the data pointed (100 int elements) but the pointer itself, whose space requirements are just 4/8 bytes (32/64 bit architectures)

In the case of complex types, the space requirements of the structure / class may be higher than the sum of the sizes of the elements due to alignment issues:

```

struct T // 64 bits architecture, g++3.4 with default options
{
   char a; // 1
   int b;  // 4
   char c; // 1
   int* d; // 8
};
struct T2
{
   int a;  // 4
   int b;  // 4
};
int main()
{
   std::cout << sizeof(T);  // 24!!! 
   std::cout << sizeof(T2); // 8
}

```

Back to the original issue of how argv is used. The first parameter, argc, is the number of elements in the array. There is also a warranty that the argv array of pointers has argc + 1 elements, the last of which is 0 (NULL), so you can ignore argc and just iterate --not that it is worth it.

```

$ myprogram arg1 "another arg"
argc: 3
argv -> [ xxxx ] -> "myprogram"
        [ xxxx ] -> "arg1"
        [ xxxx ] -> "another arg"
        [    0 ]

```

argv points to an array of pointers (xxxx) whose elements point to C strings containing the program name and arguments. An extra pointer is allocated at the end of argv array and gets 0 as value.

---

### Post by ChrisBookwood on 2008-10-15
Ahh, that actually makes sense. And thank you for explaining it so concrete!

I actually found another way, by using vector instead of an array, and it works much easier. Still thanks, though. Didn't know that was how sizeof() worked.

---

