---
title: "Using variable length C array with execvp function"
date: 2012-06-20
forum: Programming Talk
---

### Post by bluedalmatian on 2012-06-20
Im wanting to use execvp to run a command. The problem is that it requires a const pointer to an array which in all the examples I can find is allocated on the stack like this:

```
char *const args[]={"progname","arg1","arg2",0};
```

However my program will not know until runtime how many arguments there will be hence I need to allocate an array on the heap but doing this means I cant declare the pointer early on and keep the pointer constant.

I have the args stored in a c++ vector but because execvp requires a constant pointer I dont see any way of copying them into a suitable array.

Hope that makes sense?

Thanks in advance

---

### Post by Bachstelze on 2012-06-20
Are you doing C or C++, then?

---

### Post by MadCow108 on 2012-06-20
that execvp declares its interface as char * const only means that it will not modify the values in the array.
It does not mean you have to pass in something const.

const is just an annotation, it has not representation in the binary/abi

---

### Post by bluedalmatian on 2012-06-20
> **Bachstelze said:**
> Are you doing C or C++, then?

C++ but I need to get the strings into a C array to use the exec functions.

---

### Post by bluedalmatian on 2012-06-20
> **MadCow108 said:**
> that execvp declares its interface as char * const only means that it will not modify the values in the array.
It does not mean you have to pass in something const.

const is just an annotation, it has not representation in the binary/abi

ah right. thanks for that tip.

what would I declare the array as then in order than I can copy a series of variable length strings from the vector into it.

Ive tried:
```

char** args; 
args = new char*[words.size()];

```

But then when I try to copy the string out of the vector with
```
args[x]=(const char*)words[x].c_str();

```

I get an error 
invalid conversion from &#8216;const char*&#8217; to &#8216;char*

words is a C++ vector of std::strings

---

### Post by trent.josephsen on 2012-06-20
Because args[x] is a pointer to char and you're trying to give it the value of a pointer to const char. If it worked, then you could write to memory that was supposed to be labeled readonly (which is what 'const' really means).

If you want args[x] to be a pointer to const char so that the assignment works, then you need to declare args as a pointer to pointer to const char: `char const **args;`

I'm a little puzzled as to why you would think this was necessary in the first place. Just take the cast out. (Casts are rarely necessary and often indicative of poor design.)

---

### Post by dwhitney67 on 2012-06-21
> **bluedalmatian said:**
> 
what would I declare the array as then in order than I can copy a series of variable length strings from the vector into it.


This works for me:
```

#include <string>
#include <vector>
#include <iostream>
#include <unistd.h>
#include <cstring>

int main()
{
    std::vector<std::string> args;
    args.push_back("ls");
    args.push_back("-l");

    const size_t array_size = args.size();

    char** arg_array = new char*[array_size + 1];  // extra space for terminating NULL

    for (size_t i = 0; i < array_size; ++i)
    {
        arg_array[i] = strdup(args[i].c_str());
    }
    arg_array[array_size] = 0;

    execvp(arg_array[0], arg_array);

    std::cout << "This statement is never reached." << std::endl;
}

```

---

