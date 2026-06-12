---
title: "Checking output stream in C"
date: 2011-06-18
forum: Programming Talk
---

### Post by zobayer1 on 2011-06-18
I am trying to write a C program that will determine whether the program's output is tied to the terminal or it is redirected to some other file descriptor.

I thought of comparing fileno(stdout) with STDOUT_FILENO, but that will not work in case of redirection, as most of the redirections are handled with dup2.

To be more clear, what I want to do is, say, if I run my program in terminal, it will print:
```

Hello World

```But if I redirect it to some file, it will write to the file:
```

Hello
World

```I know it can be done, but just can't find out how. Any help will be appreciated.

---

### Post by zobayer1 on 2011-06-18
Looks like ubuntu forum is a lucky place, I just got the answer after posting this. It can be checked by isatty() function:
```

#include <unistd.h>
#include <stdio.h>

int main() {
        if(isatty(fileno(stdout))) printf("Yes\n");
        else printf("No\n");
        return 0;
}

```

Here is how it runs:
```

zobayer@zobayer:~/Lab/system/ls$ g++ test.cpp
zobayer@zobayer:~/Lab/system/ls$ ./a.out
Yes
zobayer@zobayer:~/Lab/system/ls$ ./a.out > out.txt
zobayer@zobayer:~/Lab/system/ls$ cat out.txt
No
zobayer@zobayer:~/Lab/system/ls$

```

Visit [http://linux.die.net/man/3/isatty](http://linux.die.net/man/3/isatty) to know about isatty() or write in terminal: man 3 isatty

Hope this will be helpful if anyone looks for it in future.

---

