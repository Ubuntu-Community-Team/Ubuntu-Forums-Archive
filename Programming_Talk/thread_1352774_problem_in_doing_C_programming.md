---
title: "problem in doing C programming"
date: 2009-12-12
forum: Programming Talk
---

### Post by mukulverma2408 on 2009-12-12
Hello friends,

I am all new to ubuntu, i want to do c programming in this new envorment the procedure that i am following is as follows:

step1: open gedit text editor.
step2: type the text
 #include<stdio.h>
#include<conio.h>
void main()
{
     printf("my name is mukul");
     exit(0);
}

step3: goto terminal and typed follwing to compile 
mukul@mukul-desktop:~$ gcc -o hello hello.c

[SIZE=2][COLOR=DarkOrange]this is the error that is appearing:[SIZE=2]
[/SIZE][SIZE=2][COLOR=Black]hello.c:2:18: error: conio.h: No such file or directory[/COLOR][/SIZE]
[/COLOR][/SIZE][SIZE=2]hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘exit’
[/SIZE]
[SIZE=3][COLOR=Green]please help me out with this i am very keen to work on ubuntu. [/COLOR][/SIZE]

---

### Post by Physical Hook on 2009-12-12
conio.h is an MS-DOS header. Remove it and see what happens.

---

### Post by Kimm on 2009-12-12
> **Physical Hook said:**
> conio.h is an MS-DOS header. Remove it and see what happens.

Its also completely redundant in that code :) so no need to keep it.

---

### Post by nvteighen on 2009-12-12
Several issues there.

0) Use the [ code] [/ code] tags (erase the space) to post code. It looks much nicer :)
1) **conio.h** is MS-DOS specific and irrelevant as others have said above.
2) **void main()** is plainly incorrect. I don't know where that comes from, not even know if it was valid in C some time ago or not. But, nowadays C uses the following signatures for main: **int main(void)** or **int main(int, char **)** (this last one for accepting command line arguments). Things like **int main()** are tolerated though are strictly speaking also incorrect. But **void main()** is absolutely wrong because the OS (all of them) expects main to return an integer as exit status.
3) **exit(0)**: exit() is declared in stdlib.h, which you haven't included. But, it is completely unnecessary if you write main correctly, this is, by making main return an integer. So, including stdlib.h would also be useless.

So, your code should be:
```

#include <stdio.h>

int main(void)
{
    printf("my name is mukul");
    return 0;
}

```

---

### Post by mukulverma2408 on 2009-12-13
thank you so much for your information, these r  the things that i m dying to know, u are really great....
could i take ur help on such similar issues again??

---

### Post by dwhitney67 on 2009-12-13
> **mukulverma2408 said:**
> ...
could i take ur help on such similar issues again??

This is the whole purpose of this forum; for people to help others in need.

---

