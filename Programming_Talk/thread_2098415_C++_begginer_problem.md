---
title: "C++ begginer problem"
date: 2012-12-26
forum: Programming Talk
---

### Post by yellowpaper on 2012-12-26
Hi everyone , i'm trying to understand why a program doesn't work properly.

First i have a main with this lines

```

 FILE *file=fopen("file.txt","rt");
    char line[5000];
    while(fgets(line,5000,file))
    {
        Cadena cadena(line);
    }

```Basically i read a file line by line and i create a object named cadena
with the line read in the file.

The constructor and destructor is like this

```

Cadena::Cadena(char *line)
{
    cadena=new char[strlen(line)];
    strcpy(cadena,line);
}

Cadena::~Cadena()
{
        delete [] cadena;
}
```When in object Cadena cadena is a char *

But when i run this program i obtain errors like this

```

*** glibc detected *** ./Nuevo: double free or corruption (!prev): 0x000000000111c250 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7eb96)[0x7f56a63f9b96]
./Nuevo[0x401d71]
./Nuevo[0x401061]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f56a639c76d]
./Nuevo[0x400f29]
```If i change the file i obtain another error , different , but with the same
characteristics.
If i comment the only line that conform the destructor the program runs well but this isn't the idea. 

I'm doing something wrong and i can't figured out.

So anyone can tell me?

---

### Post by spjackson on 2012-12-26
```

Cadena::Cadena(char *line)
{
    cadena=new char[strlen(line)];
    strcpy(cadena,line);
}

```
This is a basic C error: you need to add 1 for the nul byte, i.e.

```

    cadena=new char[strlen(line) + 1];

```
However, since you are using C++, why aren't you using std::string?

---

### Post by dwhitney67 on 2012-12-26
> **yellowpaper said:**
> 
So anyone can tell me?

Why are you mixing C and C++ constructs?  C++ was developed in the hopes of staving off the issues that you are encountering by messing with char arrays.  Just use the STL string:

```

#include <string>

class Cadena
{
public:
    Cadena(const char* str);

private:
    std::string cadena;
};

Cadena::Cadena(const char* str)
    : cadena(str)
{
}

```

---

### Post by yellowpaper on 2012-12-26
spjackson LOT of THANK YOU!...and dwhitney67 thank you too

```
However, since you are using C++, why aren't you using std::string? 	
```

```
Why are you mixing C and C++ constructs?  C++ was developed in the hopes  of staving off the issues that you are encountering by messing with  char arrays.  Just use the STL string:
```

In first place i mix C with C++ "POR QUE SOY MUY MACHO" (in English Because I am very male , it is only a joke).
 Really i programmed for a very long time with C and all this functions (strlen strcpy and so on ) I developed  for my projects , and this time is for a academic projectl. But i didn't remeber about strlen , im such an idiot...i knowed that it was a very stupid error but was so stupid that i cannot figured out.


thank you thank you and another time thank you....


If there would put a smiley dancing

---

