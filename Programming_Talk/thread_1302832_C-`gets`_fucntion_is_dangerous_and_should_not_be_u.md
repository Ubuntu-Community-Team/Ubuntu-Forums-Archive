---
title: "C-`gets` fucntion is dangerous and should not be used?"
date: 2009-10-27
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-10-27
```

#include <stdio.h>
#define MAX 81
int main()
{
    char str1[MAX];

    printf("Hello, what's your name?\n");
    gets(str1);
    /*for(int i = 0; i != '\0'; i++)
        printf("str1[%d] = %c:\t %p", i, str1[i], &str1[i]);*/

    printf("Hello %s.\n\n", str1);
    return 0;
}

```

For some reason, right after the gets function the program terminates.  As well, on compile I get a warning saying that the gets function is dangerous and should not be used. 
Any body know why this is?

---

### Post by Arndt on 2009-10-27
> **c0mput3r_n3rD said:**
> ```

#include <stdio.h>
#define MAX 81
int main()
{
    char str1[MAX];

    printf("Hello, what's your name?\n");
    gets(str1);
    /*for(int i = 0; i != '\0'; i++)
        printf("str1[%d] = %c:\t %p", i, str1[i], &str1[i]);*/

    printf("Hello %s.\n\n", str1);
    return 0;
}

```

For some reason, right after the gets function the program terminates.  As well, on compile I get a warning saying that the gets function is dangerous and should not be used. 
Any body know why this is?

It's because the user can send an unlimited amount of text, which will overwrite the buffer meant for it. This can change the values of other variables. It's a security risk, since with careful study of the program, an attacker can thereby place executable code in memory and arrange so that code is called. Then anything can happen.

---

### Post by c0mput3r_n3rD on 2009-10-27
So should I just use the fgets function instead?

---

### Post by Arndt on 2009-10-27
> **c0mput3r_n3rD said:**
> So should I just use the fgets function instead?

Yes.

---

### Post by c0mput3r_n3rD on 2009-10-27
Cool thank you :)  I'll just forget about gets.

---

### Post by muntasir_120 on 2009-10-27
The program works fine (as long as I enter less than 80 char strings) on my machine. But valid point on gets though.

---

### Post by SunSpyda on 2009-10-27
Or scanf with a limiter on it...

[php]
#include <stdio.h>
#include <stdlib.h>

#define NAME_LENGTH 80

int
main(void)
{
    char name[NAME_LENGTH];
    printf("What's your name? - ");
    scanf("%NAME_LENGTHs", name);
    if (name[strlen(name) - 1] == '\n')
        name[strlen(name) - 1] = '\0';
    printf("Hi, %s!\n", name);
    return EXIT_SUCCESS;
}
[/php]

Be aware that overflows can happen all over the place in C, & that gets() is just 1 cause. Note that overflows can also be heap and BBS based, not just stack.

---

