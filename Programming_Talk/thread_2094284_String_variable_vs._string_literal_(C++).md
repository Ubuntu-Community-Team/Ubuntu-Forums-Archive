---
title: "String variable vs. string literal (C++)"
date: 2012-12-13
forum: Programming Talk
---

### Post by uncleheinz on 2012-12-13
Hello,

I have a question related to this simple code snippet:
```


#include <iostream>
using namespace std;

int main()
    {
    string myString = "Dogg";
    string result = myString + 'y';

    cout << result << endl;

    return 0;
    }


```This current sample works flawlessly. Output is "Doggy" as expected.

But if I replace *myString* variable with a raw string
```

string result = "Dogg" + 'y';

```then it just prints out garbage.

What exactly is going on?

---

### Post by trent.josephsen on 2012-12-13
I don't know C++, but in C the expression "Dogg" + 'y' would be parsed as the sum of a char * and an integer. I would imagine overloading for the '+' operator in C++ is only defined for std::string and not for C strings (which a string literal is).

In Java, on the other hand, string literals are java.lang.String objects, and this would do what you expect.

---

### Post by ofnuts on 2012-12-13
> **uncleheinz said:**
> Hello,

I have a question related to this simple code snippet:
```


#include <iostream>
using namespace std;

int main()
    {
    string myString = "Dogg";
    string result = myString + 'y';

    cout << result << endl;

    return 0;
    }


```This current sample works flawlessly. Output is "Doggy" as expected.

But if I replace *myString* variable with a raw string
```

string result = "Dogg" + 'y';

```then it just prints out garbage.

What exactly is going on?
Crank up the warning level in your compiler and it will tell you :)

---

### Post by uncleheinz on 2012-12-13
> **ofnuts said:**
> Crank up the warning level in your compiler and it will tell you :)

Thing is, I get no warnings at all.

```

g++ -Wall -ansi -Werror file_source.cpp -o file_name

```

---

### Post by GeneralZod on 2012-12-13
Same here with g++; clang spots the problem, though:

```

clang++ -Wall filename.cpp -o filename
filename.cpp:6:28: warning: adding 'char' to a string does not append to the string [-Wstring-plus-int]
    string result = "Dogg" + 'y';
                    ~~~~~~~^~~~~
filename.cpp:6:28: note: use array indexing to silence this warning
    string result = "Dogg" + 'y';
                           ^
                    &      [    ]
1 warning generated.

```

---

### Post by dwhitney67 on 2012-12-13
g++ does not produce a warning.  I cannot be exactly certain as to why this is so because it would seem that it is an error, but it may be that the compiler is performing "pointer" arithmetic first, then assigning the result to the string.

The tiny program demonstrates the "pointer" arithmetic:
```

#include <string>
#include <cstdio>

int main()
{
    std::string result = "foo" + 'y';

    printf("addr of literal foo is %p\n", "foo");
    printf("addr of foo + 'y' is %p\n", "foo" + 'y');
}

```
This is the output:
```

addr of literal foo is 0x400972
addr of foo + 'y' is 0x4009eb

```
Basically, as it would seem, the address of the string literal "foo" is being incremented by 121 bytes, which due to no coincidence, it the decimal value of the ASCII character 'y'.

Thus it would seem that the string 'result' is being initialized to the garbage that lies 121 bytes from the beginning address of the literal "foo".

---

### Post by SledgeHammer_999 on 2012-12-14
I know that this doesn't answer the original question (which was answered adequately by **dwhitney67**), but if you wanted to have the same behavior but not use a temporary variable then you can do it this way:

[php]#include <iostream>

int main()
    {    
    std::string result = std::string("Dogg") + 'y';
    std::cout << result << std::endl;

    return 0;
    }[/php]

---

