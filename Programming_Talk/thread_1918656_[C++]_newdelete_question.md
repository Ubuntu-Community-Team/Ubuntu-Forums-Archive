---
title: "[C++] new/delete question"
date: 2012-02-01
forum: Programming Talk
---

### Post by t1497f35 on 2012-02-01
Hi,
```

#include <iostream>

int main(int argc, char *argv[]) {
    char *str = new char(15);
    str[0] = 'a';
    
    std::cout << "value: \"" << str << "\"" << std::endl;
    
    delete [] str;
    
    return 0;
}

```Afaik for a dynamic array we use **new** with square brackets, but in this example **new** also works with round brackets (but it still creates a dynamic array, right?), can anyone explain why it works? Is this wrong?

---

### Post by Zugzwang on 2012-02-01
> **t1497f35 said:**
> Hi,
```

#include <iostream>

int main(int argc, char *argv[]) {
    char *str = new char(15);
    str[0] = 'a';
    
    std::cout << "value: \"" << str << "\"" << std::endl;
    
    delete [] str;
    
    return 0;
}

```Afaik for a dynamic array we use **new** with square brackets, but in this example **new** also works with round brackets (but it still creates a dynamic array, right?), can anyone explain why it works? Is this wrong?

The constructor with round brackets will allocate *one* character and initializes it with the value 15. This is like allocating an object and using its constructor in C++. But then, you overwrite this one element with 'a' in the next line (str[0] will yield the same lvalue as *str). Since the string is not 0-terminated, in the "std::cout << ..." line, the program can either crash, output garbage, or if you are (un)lucky, just print out 'a'. In any case, calling delete[] with a non-array as you allocate here should not be done.

---

### Post by t1497f35 on 2012-02-01
Thanks, but assigning more values works just as fine.. here:

```

#include <iostream>

int main(int argc, char *argv[]) {
    char *str = new char(15);
    str[0] = 'a';
    str[1] = 'b';
    str[2] = 'c';
    str[3] = 'd';
    //etc
    
    std::cout << "value: \"" << str << "\"" << std::endl;
    
    delete [] str;
    
    return 0;
}

```It prints abcd, so I still wonder why it works..

---

### Post by 3Miro on 2012-02-01
The first "new" allocates a new location somewhere in memory. The  str[1] address is just the next address. The problem is that you don't know if the next address will be part of your program's memory or whether it will contain something important. The result should be that every now and then, if you run the program, you should get "segfault" errors. If you try to write more values, it certainly will "segfault".

Many things with new and delete can randomly work or fail. You need to be careful.

---

### Post by t1497f35 on 2012-02-01
Thanks all

---

