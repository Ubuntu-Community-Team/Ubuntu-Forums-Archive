---
title: "Segmentation Fault?"
date: 2009-10-10
forum: Programming Talk
---

### Post by Jekshadow on 2009-10-10
For some reason, whenever I run the program, I get a segmentation fault.

It is simply a weak encryption program, it is not meant for anything that I would not send in plaintext.

Here is the output from GNU Debugger:

```

me@ubuntu:~/Documents/Projects/Crypt/smthse$ gdb
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
(gdb) file ./a.out
Reading symbols from /home/me/Documents/Projects/Crypt/smthse/a.out...done.
(gdb) run
Starting program: /home/me/Documents/Projects/Crypt/smthse/a.out 

Program received signal SIGSEGV, Segmentation fault.
0x0000000000400833 in encrypt (string=0x400a54 "Hello World") at encrypt.cpp:16
16			while (string[x]) {
(gdb) q
The program is running.  Exit anyway? (y or n) y

```

The program was compiled with:
```
g++ -g encrypt.cpp
```

And the code is:

```
#include <iostream>
using namespace std;

char* encrypt(char* string) {
	char* alphabet[4];
	alphabet[0] = "bcdefghijklmnopqrstuvwxyza";
	alphabet[1] = "cdefghijklmnopqrstuvwxyzab";
	alphabet[2] = "qwertyuiopasdfghjklzxcvbnm";
	alphabet[3] = "mnbvcxzlkjhgfdsapoiuytrewq";
	char* nString;
	
	if (string == NULL || string == "")
		return "ERR: No string to encrypt!";
	int x, y = 0;
	while (alphabet[y]) {
[COLOR="Red"]		while (string[x]) {[/COLOR]
			char let = string[x];
			int letV = (int) let;
			nString[x] = alphabet[y][letV];
			x++;
		}
		y++;
	}
	return nString;
}

int main() {
	char* tmp = encrypt("Hello World");
	cout << tmp;
	return 0;
}

```

---

### Post by jacensolo on 2009-10-10
I just glanced over it, and this isn't the cause of the problem, but  tmp should be dereferenced before it is printed to the console; otherwise, you are printing the address of tmp.

---

### Post by korvirlol on 2009-10-10
im a bit rusty on my c syntax, but it doesnt look like you initialized "x". it contains whatever is in memory at the current time that it is instantiated.

try:

int x = 0, y = 0;

---

### Post by Jekshadow on 2009-10-10
> **korvirlol said:**
> im a bit rusty on my c syntax, but it doesnt look like you initialized "x". it contains whatever is in memory at the current time that it is instantiated.

try:

int x = 0, y = 0;

I changed it to "int x = 0, y = 0;" and it still gave the same segmentation error.


> **jacensolo said:**
> I just glanced over it, and this isn't the cause of the problem, but tmp should be dereferenced before it is printed to the console; otherwise, you are printing the address of tmp.

I'm not using pointers, "char* var = "test";" is the same as "char var[] = "test";", as I understand it.

I think you were thinking of if I had done something such as:

char *tmp

---

### Post by shadylookin on 2009-10-10
It's been a while since I've done any c/c++ but

x isn't initialized so it probably starts off as something outside the bounds. 

also will this while (string[x]) ever terminate? since c will let you go out of bounds on arrays shouldn't you pass a size and keep x from going beyond that.

Also since you're using c++ doesn't it have a handy string class for this stuff?

---

### Post by lswb on 2009-10-10
I may be off base here, but it appears to me that on entry to your encrypt() function, the local variable char* nString; does not point to any particular place. In the loop in the same function you do an assignment

nString[x] = alphabet[y][letV]; 

and since nString is just some random pointer, it segfaults.

What's more, you are returning nString from the function, returning a local variable is a no-no.

If this is indeed the reason for the segfault, a simple (perhaps not the best way) to avoid it would be to declare nString like this:

static char nString[SomeBigEnoughNumber];

---

### Post by nvteighen on 2009-10-11
There are several issues there. The most important is that in C++ you should avoid C-style strings and learn how to use C++ strings, which are really much easier to manipulate.

Compiling using the -Wall flag will reveal some issues. And you're failing to allocate memory and to check array bounds (something that std::string's will make easier).

Also, avoid "using namespace std"... If you happen to use std::string's, your string variable will clash against the string class... :P

---

### Post by Arndt on 2009-10-11
> **nvteighen said:**
> There are several issues there. The most important is that in C++ you should avoid C-style strings and learn how to use C++ strings, which are really much easier to manipulate.

Compiling using the -Wall flag will reveal some issues. And you're failing to allocate memory and to check array bounds (something that std::string's will make easier).

Also, avoid "using namespace std"... If you happen to use std::string's, your string variable will clash against the string class... :P

I recommend walking through the code with the gdb 's' command, after all, it's not long. There are some aha experiences waiting.

---

### Post by Can+~ on 2009-10-11
[PHP]	char* alphabet[4];
	alphabet[0] = "bcdefghijklmnopqrstuvwxyza";
	alphabet[1] = "cdefghijklmnopqrstuvwxyzab";
	alphabet[2] = "qwertyuiopasdfghjklzxcvbnm";
	alphabet[3] = "mnbvcxzlkjhgfdsapoiuytrewq";
	char* nString;[/PHP]

Not sure if you can do that.

[PHP]
char *nString;
...
nString[x] = alphabet[y][letV];[/PHP]

nString is a plain pointer to nowhere. You're trying to write to an unknown direction, and to an unreserved space, either malloc, use string, or use a stack char[] array like you did before (but better).

[PHP]while (alphabet[y]) {[/PHP]

What's the condition here? Let's assume that alphabet is correct and it does store everything you mentioned above, when it would end?

If you wish to keep this, add something like (and expand alphabet maximum size by one) alphabet[4] = NULL;

[PHP]int letV = (int) let;
nString[x] = alphabet[y][letV];[/PHP]

ASCII goes from (unsigned) 0 to 255, and the most common characters go from 32 onwards. So you'll be trying to access more than the size of your array of letters.

[PHP]return nString;[/PHP]

Returning a pointer to a local variable? That won't work.

All of this are possible causes of Segmentation Fault.

I would suggest you to start reading a tutorial or start with an easier language (Forum's choice: Python).

---

### Post by napsy on 2009-10-11
[PHP]char* alphabet[4]; 
    alphabet[0] = "bcdefghijklmnopqrstuvwxyza"; 
    alphabet[1] = "cdefghijklmnopqrstuvwxyzab"; 
    alphabet[2] = "qwertyuiopasdfghjklzxcvbnm"; 
    alphabet[3] = "mnbvcxzlkjhgfdsapoiuytrewq"; 
    char* nString;[/PHP]

This is legal. It's an array of string literals. But you can't change the strings.
[PHP]
while (alphabet[y])[/PHP]

This is valid since c strings are NUL-terminated. The loop will end when NUL (which is 0 in ascii) is reached.

[PHP]
return nString;  
[/PHP]

This is a correct way to return a pointer to char.n But you have to allocate memory for it.

---

### Post by Can+~ on 2009-10-11
> **napsy said:**
> [PHP]char* alphabet[4]; 
    alphabet[0] = "bcdefghijklmnopqrstuvwxyza"; 
    alphabet[1] = "cdefghijklmnopqrstuvwxyzab"; 
    alphabet[2] = "qwertyuiopasdfghjklzxcvbnm"; 
    alphabet[3] = "mnbvcxzlkjhgfdsapoiuytrewq"; 
    char* nString;[/PHP]

This is legal. It's an array of string literals. But you can't change the strings.


Good to know.
> **napsy said:**
> 
[PHP]while (alphabet[y])[/PHP]

This is valid since c strings are NUL-terminated. The loop will end when NUL (which is 0 in ascii) is reached.

It's not valid, since it's accessing the array of strings, not the strings itself:

alphabet[3] = "mnbvcxzlkjhgfdsapoiuytrewq";

That's the last "string", it ends in '\0' as it should, but the problem is, is that the iterator (y) goes, it will try to access the alphabet[4] which does not exist (it goes beyond the total length of the char* array). You can even run that single piece of code and get a segfault (I just tried).

> **napsy said:**
> 
[PHP]
return nString;  
[/PHP]

This is a correct way to return a pointer to char.n But you have to allocate memory for it.

Of course it is a correct way to return a char*, I already mentioned before that said string wasn't allocated anywhere.

---

### Post by Iceberg398 on 2009-10-13
> **Jekshadow said:**
> I'm not using pointers, "char* var = "test";" is the same as "char var[] = "test";", as I understand it.

I think you were thinking of if I had done something such as:

char *tmp

In C an array is simply a pointer to the first element, so int* x and int x[] are the same, because x is an integer pointer either way.

You declare char* nString which is a character pointer not pointing to anything, then you use nString[x] which is the same as *(nString + x), which is a pointer to nothing in particular, giving you a segmentation fault.

Long story short, you need to assign memory for your array and point nString to the start of it.

---

### Post by Arndt on 2009-10-14
> **Iceberg398 said:**
> In C an array is simply a pointer to the first element, so int* x and int x[] are the same, because x is an integer pointer either way.

You declare char* nString which is a character pointer not pointing to anything, then you use nString[x] which is the same as *(nString + x), which is a pointer to nothing in particular, giving you a segmentation fault.

Long story short, you need to assign memory for your array and point nString to the start of it.

We are probably muddying the issue for the OP, but as declarations, int *x and int x[] are not the same. x, when used as an expression, will be a pointer to int; that is true.

---

### Post by napsy on 2009-10-14
> **Iceberg398 said:**
> In C an array is simply a pointer to the first element, so int* x and int x[] are the same, because x is an integer pointer either way.

You declare char* nString which is a character pointer not pointing to anything, then you use nString[x] which is the same as *(nString + x), which is a pointer to nothing in particular, giving you a segmentation fault.

Long story short, you need to assign memory for your array and point nString to the start of it.

As Arndt already pointed out, an int pointer and int array are not the same. An array is not a storage for memory addesses. You can picture an array as sequenced data.

---

### Post by Iceberg398 on 2009-10-14
> **napsy said:**
> As Arndt already pointed out, an int pointer and int array are not the same. An array is not a storage for memory addesses. You can picture an array as sequenced data.

Yes, but isn't the name of an array simply a pointer to the first element of that array?  I'm learning C at the moment and want to be sure I understand it correctly.

if you do something like...

int x[5]

you get an array of 5 ints, but if you go and call 

x[5] what you're actually getting is *(x + 5) this is why 5[x] is the same as x[5]

x itself is just a pointer to x[0]

When you actually initialize an array you're getting sequenced data, but the actual variable itself is just a pointer to that data.

**EDIT: Played around with it a bit and I think I understand it better, while x acts as a pointer, it's not legal to actually use it as a pointer variable (eg assigning other pointer values to it).  Which leads into my next question...**

Also, I'm learning C90 in which x[] isn't even legal code, so I'm not sure what it does at compile time.  If you declare x[] and don't initialize it to anything I would assume that the compiler would simply set aside the x array pointer, but not actually have it pointing to anything until you allocate memory for it during runtime.  It doesn't seem like the compiler has any way of allocating memory on the stack for x, so it would seem like the only other option would be for it to intelligently include malloc() calls and set aside memory on the heap at runtime.

Am I right on this?

---

### Post by Can+~ on 2009-10-14
> **Iceberg398 said:**
> 
**Also, I'm learning C90 in which x[] isn't even legal code, so I'm not sure what it does at compile time**.  If you declare x[] and don't initialize it to anything I would assume that the compiler would simply set aside the x array pointer, but not actually have it pointing to anything until you allocate memory for it during runtime.  It doesn't seem like the compiler has any way of allocating memory on the stack for x, so it would seem like the only other option would be for it to intelligently include malloc() calls and set aside memory on the heap at runtime.

Am I right on this?

It does nothing, it aborts compilation

```
canxp@asgard:~/Desktop$ gcc -std=c99 asdf.c -o asdf
asdf.c: In function ‘main’:
asdf.c:31: error: array size missing in ‘x’
```

---

### Post by Iceberg398 on 2009-10-15
Right, thanks.  I was under the false impression that you could declare arrays of unspecified length in C99.  Things make much more sense now:P

---

### Post by Arndt on 2009-10-15
> **Iceberg398 said:**
> Right, thanks.  I was under the false impression that you could declare arrays of unspecified length in C99.  Things make much more sense now:P

The above is true, but you can use the construct "int x[]" in two ways: when declaring arguments to a function, and if you have an initializer, as in int x[] = {1,4,9}. When used for declaring an argument, it means exactly the same thing as "int *x".

```
int main(int argc, char *argv[])
int main(int argc, char **argv)

```
To some people, the former is a reminder that argv is an array, not just some arbitrary pointer.

---

