---
title: "Compiling error"
date: 2015-01-26
forum: Programming Talk
---

### Post by Nilupul_Sandeepa on 2015-01-26
hey, I'm new to Ubuntu and c programming. So i wrote this simple code using gedit:
```

#include <stdio.h>
void main()
{
       printf("Hello");
}
```

It shows this error when i try to compile it.

 ```
error: return type of ‘main’ is not ‘int’ [-Werror=main]
 void main()
      ^

```
Please someone can tell me what's wrong with this. Thanks in advance!!

---

### Post by spjackson on 2015-01-26
Welcome to the forums.

As you are new to C, I recommend that you learn standard C first, ignoring any additions supported by some compilers. In standard C,
> 
void main()

is not permitted. The only permitted definitions of main are:
```

int main(void)

```
and
```

int main(int argc, char * argv[])

```

main always returns an int. If you reach the end of the function it returns 0, but some consider this stylistically bad and recommend that you explicitly return a value. Thus
```

#include <stdio.h>
int main(void)
{
    printf("Hello\n");
    return 0;
}

```
If your original code comes from a tutorial then I would not recommend it.

---

### Post by Nilupul_Sandeepa on 2015-01-27
Yes it was from a tutorial. And thanks for letting me know what's wrong with my code. It was really helpful. I really appreciate  that. :)

---

### Post by Matthew_Harrop on 2015-01-27
If you need some help with C, try this book written by its authors:
[https://archive.org/details/pdfy-Ry7HcW4yeAIEgsSM](https://archive.org/details/pdfy-Ry7HcW4yeAIEgsSM)
The downloads are on the left and are free :)

---

### Post by Nilupul_Sandeepa on 2015-01-28
Thanks for the link. I downloaded it and read few pages. And it seemed to be really helpful. Looks like i'm about to have a good C programming experience thanks to you all. :p

---

### Post by Matthew_Harrop on 2015-01-29
If you plan to do anything in C++ you can also get Bjorne Stroustrup's book.
[https://archive.org/details/TheCProgrammingLanguage4thEditionOpsylum](https://archive.org/details/TheCProgrammingLanguage4thEditionOpsylum)

---

