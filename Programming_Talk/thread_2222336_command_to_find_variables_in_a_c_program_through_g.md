---
title: "command to find variables in a c program through gcc"
date: 2014-05-06
forum: Programming Talk
---

### Post by zinat on 2014-05-06
Local Variables are stored in Stack.So is there any command or other way to find variables declared or defined in c programming using gcc or any other compiler.

---

### Post by zinat on 2014-05-06
Is there any way to find the variables declared or defined in a c program and print those variables??

for eg this is the code


```


#include<stdio.h>
 
int main()
{
   int a, b, c;
 
   printf("Enter two numbers to add\n");
   scanf("%d%d",&a,&b);
 
   c = a + b;
 
   printf("Sum of entered numbers = %d\n",c);
 
   return 0;
}


```

I want to print all the variables been used.

---

### Post by steeldriver on 2014-05-06
Threads merged

If you want to see the local variables in the current scope when the program is run, then provided it is compiled with debug symbols you could use the 'info locals' command in gdb e.g. for your code above,

```

$ gcc -O0 **-g** -Wall -o yourprog yourprog.c 

```
Then
```

$ [B]gdb yourprog
[/B]GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2.1) 7.4-2012.04
.
.
.
Reading symbols from /home/steeldriver/Documents/forums/yourprog...done.
(gdb) b 12
Breakpoint 1 at 0x80484a4: file yourprog.c, line 12.
(gdb) run
Starting program: /home/steeldriver/Documents/forums/yourprog 
Enter two numbers to add
5 7

Breakpoint 1, main () at yourprog.c:12
12       printf("Sum of entered numbers = %d\n",c);
[B](gdb) info locals
a = 5
b = 7
c = 12
[/B](gdb) 

```

OTOH if you want something that will look at your source code (.c) file and list all the variables direct from that, then I guess you would need some kind of source code analyser (or you could write your own - with a lexical analyser and parser!)

---

