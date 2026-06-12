---
title: "Array size limitation in gcc 4.1.3"
date: 2008-01-28
forum: Programming Talk
---

### Post by amuser on 2008-01-28
hI,

I was trying to declare a double array as in the code below. When the SIZE is greater than 1023 I see segmentation faults at runtime. I am using Ubuntu 7.10 and the compiler is gcc-4.1.3. Can someone tell me why this is happening and how can increase this limit?


#include <stdio.h>

#define SIZE 1023

main()
{
	double a[SIZE][SIZE];
	printf("Fine....\n");
}


Thanks,
amuser

---

### Post by lnostdal on 2008-01-28
```

#include <stdio.h>

#define SIZE 1024

int main()
{
  double a[SIZE][SIZE];
  printf("Fine....\n");
  return 0;
}


...
...


lars@ibmr52:~/programming/c$ gcc -Wall -g a.c -o a
a.c: In function &#8216;main&#8217;:
a.c:7: warning: unused variable &#8216;a&#8217;
lars@ibmr52:~/programming/c$ ./a
Segmentation fault (core dumped)
lars@ibmr52:~/programming/c$ ulimit -s
8192
lars@ibmr52:~/programming/c$ echo "1024 * 1024" | bc
1048576
lars@ibmr52:~/programming/c$ ulimit -s 1500000
lars@ibmr52:~/programming/c$ ./a
Fine....

```

..always compile with -Wall and -g btw.

---

### Post by lnostdal on 2008-01-28
oh, but you prolly might wanna take a look at malloc
```
man 3 malloc
```

..it's standard C. short: malloc allocates memory on the heap instead of the (limited) stack.

---

### Post by hod139 on 2008-01-28
In case you do not understand lnostdal's reply, let me explain what he did.  When you allocate your 2 dimensional array like this:
  ```

   	double a[SIZE][SIZE]
 
```
you are telling the compiler to allocate this array into the stack memory.  The stack is a much more simpler part of memory to deal with, but it is also much smaller.

The system places a maximum size (not gcc) on the stack. lnostdal did some math to see how much memory was required to hold the array, and used the ulimit command to raise the maximum amount of stack memory.

As he pointed out, the better solution to raising the stack size (since this isn't always a solution) is to allocate the memory on the heap using malloc.

---

### Post by amuser on 2008-01-29
Thanks to both Inostdal and hod139.

Things are a bit more clear to me now...

Thank you very much

---

