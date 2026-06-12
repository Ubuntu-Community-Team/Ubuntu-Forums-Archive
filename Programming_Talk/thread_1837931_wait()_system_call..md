---
title: "wait() system call."
date: 2011-09-02
forum: Programming Talk
---

### Post by ankit3111 on 2011-09-02
Hello everyone,
I am stuck with wait() system call in linux.


#include<stdio.h>
#include<unistd.h>

void main()
{	
	int pid;
	if((pid = vfork()) == 0)
		execl("/bin/echo","echo","Hello There",(char *)0);
	else 
		wait();
}

OUTPUT:
Hello There

---------------------------------------------------------------

#include<stdio.h>
#include<unistd.h>

void main()
{	
	int status;
	int pid;
	if((pid = vfork()) == 0)
		execl("/bin/echo","echo","Hello There",(char *)0);
	else 
		wait(&status);
}

OUTPUT:
Hello There


//------------------------------------

The above two programs run well on my system without any compilation warning.

The difference in the two programs is that first one what call to "wait()" without any argument & the second one call it with and 'int * argument'.

How come a system call have more that one interface ?? 
Can someone please explain me whats happening ...

Thank You.

---

### Post by karlson on 2011-09-02
> **ankit3111 said:**
> Hello everyone,
I am stuck with wait() system call in linux.

The above two programs run well on my system without any compilation warning.

The difference in the two programs is that first one what call to "wait()" without any argument & the second one call it with and 'int * argument'.

How come a system call have more that one interface ?? 
Can someone please explain me whats happening ...

Thank You.

You have an implicit declaration of wait(), which linker then links to the implementation of wait provided by standard C library.  It's very likely that the call is being interpreted as wait(NULL).

I would suggest when you compile, which I assume is on Ubuntu to use -Wall flag that way you can see the warnings that are actually being suppressed.

Further read
```

man -s 2 wait

```
and include the headers it suggest that way you are not relying on compiler for interpretation of what it is that you have written.

---

### Post by Bachstelze on 2011-09-02
> **karlson said:**
> It's very likely that the call is being interpreted as wait(NULL).


What makes you think that? I think it's very likely that you are wrong.

*EDIT:* Case in point:

```
firas@applejack ~ % cat test.c                      
#include <stdio.h>

int main(void)
{
        foo();
        return 0;
}

void foo(int* p)
{
        printf("argument is %p\n", p);
        printf("NULL is %p\n", (int*)NULL);
}
firas@applejack ~ % gcc -o test test.c 
test.c:9:6: warning: conflicting types for &#8216;foo&#8217;
test.c:5:9: note: previous implicit declaration of &#8216;foo&#8217; was here
firas@applejack ~ % ./test 
argument is 0x1
NULL is (nil)
firas@applejack ~ % gcc -m32 -o test test.c
test.c:9:6: warning: conflicting types for &#8216;foo&#8217;
test.c:5:9: note: previous implicit declaration of &#8216;foo&#8217; was here
firas@applejack ~ % ./test                 
argument is 0x8048410
NULL is (nil)

```

---

### Post by karlson on 2011-09-02
> **Bachstelze said:**
> What makes you think that? I think it's very likely that you are wrong.


I'll have to retest this.  The code you posted doesn't even compile for me.

---

### Post by Bachstelze on 2011-09-02
> **karlson said:**
> Can't argue with that.  I simply don't know what the behavior of wait is when there is nothing on the stack.

The point is that there is not "nothing" on the stack. ;) The function will just pick whatever is at the location where the argument is supposed to be. The code of the actual function is irrelevant, the method of argument-passing  is a convention thal *all* functions must follow (otherwise nothing could work).

---

### Post by Arndt on 2011-09-02
> **karlson said:**
> Can't argue with that.  I simply don't know what the behavior of wait is when there is nothing on the stack.

Given that nothing was pushed on the stack before the wait call pop from ESP is likely to return 0.  In other instances it might not be the case.  Don't have any other cases or wait's assembly to say otherwise.

If I am wrong I stand corrected.

The user program looks as if the process started life at the first line of 'main', but in reality 'main' is often called from a function '_start', which sets up the environment array envp, and also argc and argv. So there will be things on the stack.

Even if that was not the case, the local variable 'pid' is maybe on the stack. Only maybe, because it's actually not used at all, and can be optimized away.

If the stack is really empty when you attempt to look at an element on it, you will probably get a segmentation violation error.

---

### Post by karlson on 2011-09-02
Ok.  I am getting stupider...  Must sleep. :)

---

### Post by ankit3111 on 2011-09-02
> **Bachstelze said:**
> What makes you think that? I think it's very likely that you are wrong.

*EDIT:* Case in point:

```
firas@applejack ~ % cat test.c                      
#include <stdio.h>

int main(void)
{
        foo();
        return 0;
}

void foo(int* p)
{
        printf("argument is %p\n", p);
        printf("NULL is %p\n", (int*)NULL);
}
firas@applejack ~ % gcc -o test test.c 
test.c:9:6: warning: conflicting types for &#8216;foo&#8217;
test.c:5:9: note: previous implicit declaration of &#8216;foo&#8217; was here
firas@applejack ~ % ./test 
argument is 0x1
NULL is (nil)
firas@applejack ~ % gcc -m32 -o test test.c
test.c:9:6: warning: conflicting types for &#8216;foo&#8217;
test.c:5:9: note: previous implicit declaration of &#8216;foo&#8217; was here
firas@applejack ~ % ./test                 
argument is 0x8048410
NULL is (nil)

```

This Worked for me.
thanks a lot !!!

This works as long as the prototype for foo [void foo(int* p);] is not declared at the start, once it is declared the program won't compile giving error message "too few arguments to function &#8216;foo&#8217;".

The same is the case with wait();
until we omit the statement #include<wait.h> "wait()" would work perfectly fine without any warning, but once we have included the include statement the program won't compile giving error message "too few arguments to function &#8216;wait&#8217;".

Thank you Mr.Firas for the help.

---

### Post by Bachstelze on 2011-09-02
> **ankit3111 said:**
> This Worked for me.
thanks a lot !!!

It was just an example, you should never do that!

---

