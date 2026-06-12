---
title: "Segmentation Fault when Dereferencing a pointer in C"
date: 2007-02-03
forum: Programming Talk
---

### Post by prodonjs on 2007-02-03
I'm really stumped on an issue I'm having with a project for class. I'm a third year CS student and part of our graduation requirements entail us doing a fairly in depth development project. Mine and a partner's task is to implement an updated version of the Accelerated GCD algorithm in the GMP MP Library. It should be a really rewarding project and our goal is to ascertain whether or not this updated algorithm will perform better under RSA sized inputs (since the Extended GCD algorithm is commonly used in RSA encryption and decryption).

Anyways, I'm having an issue trying to return a value from a function in our gcd.c file.

Here is what I want to do:
I have a method called find_a that returns a mp_limb_t value (which is equivalent in precision to a standard int type). What I need to do though is modify that function to not only return that value, but also a correlating value so I plan to do that through an out-mode parameter in the function parameter list. I am using the following syntax:

mp_limb_t find_a (mp_ptr n1p, ....) where mp_ptr is defined as mp_limb_t * in the gmp.h header file.

Inside of the function body I am trying to dereference the pointer and assign it a limb value so I am saying:

*n1p = n1_l;

When I run this program I get a segmentation fault and I really don't know what the problem could be.

I know I should be able to do this because I wrote a small dummy program to test what I wanted to do and it worked fine. Here is the code:

#include <stdio.h>

typedef int * 		int_ptr;

int ptrFunc(int_ptr r, int n) {
	*r = n * 2;
	return n - 10;
}

int main(void) {
	int x, z;
	int_ptr y;

	x = 45;

	printf("Before ptrFunc: x=%d, y=%d, z=%d\n", x, *y, z);
	z = ptrFunc(y, x);
	printf("After ptrFunc: x=%d, y=%d, z=%d\n", x, *y, z);
}

And my output is: 
Before ptrFunc: x=45, y=0, z=0
After ptrFunc: x=45, y=90, z=35
     23905:
     23905:     calling fini: /lib/tls/i686/cmov/libc.so.6 [0]
     23905:

Now that last part is confusing me too, and perhaps that is where my error is coming from. I don't know what the problem is but I have stared at it all day and maybe you guys can help me out. Two eyes are always better than one.

As if you can't tell, C is not my native language. I started programming in Java and I am one of the people who believes object-orientated style is the most natural way to program. C is nothing more than glorified assembly language to me but it's a lot of fun to learn and experiment in an unfamiliar language. Thanks for any help anyone can provide.

---

### Post by jblebrun on 2007-02-03
If you're getting a segfault, then the pointer holds a value that points to an unallocated address, or is null. 

Compile the program with debugging symbols (gcc -g). Run the program in the debugger. When it segfaults, you'll get a debugger prompt, where you can print the value of the pointer of interest, to verify that it points to a valid memory location.

---

### Post by lnostdal on 2007-02-03
i'm to tired to give a detailed response but i'll scribble down some general stuff..

if your real application (not the example you pasted) has a lot of context (potential places for error) that requires setting up before reaching the spot where the error actually occurs try setting a breakpoint just before the error occurs then examining the state of all context .. DDD is great for this kind of work ..  when you see something that does not make sense follow it backwards up the stack and/or history of calls and set new breakpoints back in time until you can pinpoint what causes this

a thing i noticed; i'm betting you are not compiling your software with -Wall because the example code you pasted would give some warnings .. in general you should always compile like this:
```
gcc -g -Wall program.c -o program
```

..because this will catch a lot of potential problems (-Wall) and generate debug-info (-g)

when i run your program i see that it segfaults (SIGSEGV) .. so i run it under gdb to see where it happens:

```

lars@ibmr52:~/programming/c$ gcc -g -Wall a.c -o a
lars@ibmr52:~/programming/c$ ./a
Before ptrFunc: x=45, y=1474660693, z=-1208946700
Segmentation fault (core dumped)
lars@ibmr52:~/programming/c$ gdb a 
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run
Starting program: /home/lars/programming/c/a 
Before ptrFunc: x=45, y=1474660693, z=-1208721420

Program received signal SIGSEGV, Segmentation fault.
0x08048360 in ptrFunc (r=0xb7f6a290, n=45) at a.c:6
6         *r = n * 2;
(gdb) bt
#0  0x08048360 in ptrFunc (r=0xb7f6a290, n=45) at a.c:6
#1  0x080483b7 in main () at a.c:18
(gdb) 

```

..which means it happens when you're calling ptrFunction from the function main at line 18, more exactly inside ptrFunc at line 6 (do note that line numbers probably will not match your code exactly so run this yourself)..

i'll just let this code and comments speak for it self:

```

#include <stdio.h>

typedef int* int_ptr;

int ptrFunc(int_ptr r, int n) {
  *r = n * 2;
  return n - 10;
}


int main() {
  int tmp;
  int x, z;
  int_ptr y;

  // `y' does not point to any allocated or static memory!
  // it points to some random location which you cannot assign to or access safely!
  // see: http://en.wikipedia.org/wiki/Protected_Mode
  // and: http://en.wikipedia.org/wiki/SIGSEGV

  // here is one way of fixing this by telling y to point to tmp which is "safe memory"
  // inside our process:
  y = &tmp;
  
  x = 45;
  
  printf("Before ptrFunc: x=%d, y=%d, z=%d\n", x, *y, z);
  z = ptrFunc(y, x);
  printf("After ptrFunc: x=%d, y=%d, z=%d\n", x, *y, z);
  return 0;
}


/*
  lars@ibmr52:~/programming/c$ gcc -g -Wall a.c -o a

  lars@ibmr52:~/programming/c$ ./a
  Before ptrFunc: x=45, y=-1077418692, z=-1208295436
  After ptrFunc: x=45, y=90, z=35



  note that the variables are not initialized to 0
*/

```

..and one more thing; object orientation is definitively not the most natural way to program.. it is just _one single_ way of looking upon design and solutions .. there are many and no single one of them is the "most natural way"

the most natural way to program is using language oriented programming.. as bruce lee stated; "have no style - be formless like water"  (or similar) he was probably talking about a programmable programming language like lisp :)

---

### Post by prodonjs on 2007-02-04
Hey man thanks a ton. I had a feeling the problem was by not explictly assigning the pointer a value before trying to dereference it. I assumed incorrectly that when you declared a pointer, the pointer itself was located in visible accessible memory and then you could assign it's reference value as you wished. Actually the way I am doing it now is more intuitive because I have a mp_limb_t value called n1, and now I just make the mp_ptr = &n1 inititially and I have an alias for n1 that I can use simply for an outmode parameter.

Thanks a million for your kindly consideration. That's what I love so much about coming to active boards such as these, people are always willing to lend a hand. 

By the way, I've done some Prolog and Haskell development and I must say that Haskell is a pretty neat language once you get used to the functional style. I suppose each has his own, but I can agree with your sentiments about a programmable language that lets you be free to use in the way most suited for you and your task.

On a side note, the way my professor told us to link against the GMP library is causing some issues. He instructed us to use this type of syntax:

/bin/sh ./libtool --mode=link gcc  -m32 -O2 -fomit-frame-pointer -mtune=pentium3 -o tester testGMP.c libgmp.la

To use libtool to link my testGMP program against the libgmp shared library. However, when I do that, the tester executable that I create shows up as a Bourne Shell Script when I 'file' it. It shouldn't be like that because then I can't run gdb with it. Any ideas on why that syntax is incorrect?

---

