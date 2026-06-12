---
title: "subtle difference between cstrings in c and c++"
date: 2009-09-22
forum: Programming Talk
---

### Post by monkeyking on 2009-09-22
Hi the following code compiles and runs with no errors in c

[PHP]
#include <stdio.h>

enum{
  lens = 4
};


int main(){
  const char nams[lens] ="four";


  return 0;
}
[/PHP]

whereas the following c++ code wont compile

[PHP]
#include <iostream>

enum{
  lens = 4
};


int main(){
  const char nams[lens] ="four";


  return 0;
}
[/PHP]

It seems the extraspace for the nullterminator in c is not needed?


Thanks in advance

---

### Post by MadCow108 on 2009-09-22
It is needed but the compiler does not warn you about it (no idea why)

the string will not be null terminated in the C example and so any use of functions dependant on null termination may corrupt your memory.

---

### Post by monkeyking on 2009-09-22
Ahh, ok thanks.

---

### Post by nvteighen on 2009-09-22
The thing is that... if you had set lens to the correct number or left it as [], the code would have worked flawlessly as the compile would have calculated the needed size by its own and put the NULL terminator automatically (as it is a stack-based allocated string).

As a besides-note, **stdio.h** and **iostream** are not needed to have C-style strings. Those are primitive data types known by the compiler. If you were trying to use C++-style strings, you would have to use the **strings** header.

Also, that enum is completely awkward... It would have been much normal to use a preprocessor macro **#define lens 4**...

```

#include <stdio.h>

int main(void)
{
    char mystring[] = "four";

    printf("String: %s\nSize of string: %d\n", mystring, sizeof(mystring));

    return 0;
}

```

---

