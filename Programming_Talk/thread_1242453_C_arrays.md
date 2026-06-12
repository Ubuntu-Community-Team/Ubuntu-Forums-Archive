---
title: "C arrays"
date: 2009-08-17
forum: Programming Talk
---

### Post by matmatmat on 2009-08-17
I want to know the size of an array without using sizeof (or anything else like it),
I have this code:
```

#include <stdio.h>

void end(char a[], int length)
{
    int retval;
    for(retval = 0; a != '\0'; a++) {retval++;printf("1");}
	int endn = retval - length;	
	char end[length];	
	int i2;
	int b = 0;
	printf("2");
	for(i2=0;i2<=retval;i2++){
		if (i2 >= endn){
			end[b]=a[i2];
			b++;
		}
	}
}

int main(int argc, char** argv)
{
	char test[] = "TEST.TXT";
    end(test, 3);
	return 0;
}

```
when run it just prints 1's

---

### Post by Drone022 on 2009-08-17
Your in an infinite loop, thats why you get 1s.

Did you mean.....

```

#include <stdio.h>

void end(char a[], int length)
{
    int retval;
    [B]for(retval = 0; a[retval] != '\0'; retval++) 
    {
      printf("1");
    }[/B]	
        int endn = retval - length;	
	char end[length];	
	int i2;
	int b = 0;
	printf("2");
	for(i2=0;i2<=retval;i2++){
		if (i2 >= endn){
			end[b]=a[i2];
			b++;
		}
	}
}

int main(int argc, char** argv)
{
	char test[] = "TEST.TXT";
    end(test, 3);
	return 0;
}

```

---

### Post by matmatmat on 2009-08-17
Thanks

---

### Post by matmatmat on 2009-08-17
How can I return a pointer to the array (so I can use printf)?

---

### Post by Drone022 on 2009-08-17
In C an array is pretty much a pointer already.

I haven't actually tried to figure out what your code is doing but here you can return a pointer and print your array 'a'

```

#include <stdio.h>

**char* **end(char a[], int length)
{
    int retval;
    for(retval = 0; a[retval] != '\0'; retval++) 
    {
      printf("1");
    }	
        
    int endn = retval - length;	
    char end[length];	
    int i2;
    int b = 0;
    printf("2");

    for(i2=0;i2<=retval;i2++)
    {
	if (i2 >= endn)
        {
	     end[b]=a[i2];
	     b++;
	}
    }
    
    **return a;**

}

int main(int argc, char** argv)
{
    char test[] = "TEST.TXT";
    **printf("%s", end(test, 3));**
    return 0;
}

```

---

### Post by Can+~ on 2009-08-17
I've been reading that code for the fifth time, and I can't make any sense of it.

For starters, C automatically appends "\0" when dealing with strings. And this functionallity already exists, it's called [FONT="Courier New"][strlen]("http://www.cplusplus.com/reference/clibrary/cstring/strlen/")();[/FONT]. And it could be coded something like:

[PHP]int getlen(char* str)
{
	int i;
	
	for (i=0; str[i] != '\0'; i++);
	
	return i;
}[/PHP]

(Alternative: pointer arithmetic)
[PHP]int getlen(char* str)
{
	char *p;
	
	for (p=str; *p != '\0'; p++);
	
	return p-str;
}[/PHP]

On the other hand, I think you wanted to do something similar but with other types (integers for example), but for integers you don't have any \0 to add at the end, as integers can take any number, and char* arrays are just a "mapping" that have \0 reserved (plus many other [control characters]("http://en.wikipedia.org/wiki/ASCII#ASCII_control_characters")).

Also, there are security implications on having things using a termination mark, when it's not present, you'll keep on reading/writing until it bumps into another thing and gets segfaulted or (Worst) replaces it without telling anyone. Main reason why it's preferred to use the strn-family rather than the str-family of functions when dealing with strings.

---

### Post by wmcbrine on 2009-08-17
> **matmatmat said:**
> I want to know the size of an array without using sizeofWhy?

You realize that sizeof isn't a real function, right? It's written like a function, but it's really an operator, and it's usually evaluated at compile time. There's no overhead.

---

### Post by nvteighen on 2009-08-17
First, there's strlen()... a well-known friend from the C Standard Library. But, if you want to reimplement it by yourself, it's ok; though it's much simpler than you think (look at Can+~'s post).

Second, **sizeof()**, as told by the others, is an operator that evaluates at compile time. And in this case, it would have been totally useless.

**sizeof()** yields the size at compile time of some data. This means that it will be accurate only for that stuff allocated at compile time and not anything allocated dynamically. I don't know whether you are familiar with dynamic memory or not, but I tell you strings can be allocated that way. As dynamic memory is always accessed through pointers, sizeof() would have reported always a size of 4 in 32-bit or 8 in 64-bit... But sizeof()  strings allocated in stack-based memory would have yielded the "correct" answer (even though they actually are pointers...).

The usual way to deal with this is to never use sizeof() into anything that is a pointer or an array to avoid possible undefined behaivor.

---

### Post by Lux Perpetua on 2009-08-17
> **nvteighen said:**
> I don't know whether you are familiar with dynamic memory or not, but I tell you strings can be allocated that way. As dynamic memory is always accessed through pointers, sizeof() would have reported always a size of 4 in 32-bit or 8 in 64-bit... But sizeof()  strings allocated in stack-based memory would have yielded the "correct" answer (even though they actually are pointers...).Not quite. Arrays and pointers are not the same. ```
char str[] = "?!";
int n = sizeof(str);
```That declares str to be an array (*not* a pointer) containing the characters '?', '!', and '\0'. As expected, sizeof(str) is then 3. ```
char *str = "?!";
int n = sizeof(str);
```That declares str to be a pointer to char, pointing to an array containing the characters '?', '!', and '\0'. Since str is simply a pointer, sizeof(str) is the size of a machine integer (4 or 8). Big difference. In the second case, str is a pointer variable, which means the compiler actually creates space for it. In the first case, the address of that array is not stored anywhere; all you get is the array itself. It's confusing because the syntax for pointers and arrays is very similar, and the name of an array can in fact be cast implicitly to the corresponding pointer value. However, it is not a pointer itself. (For example, you cannot assign to it.) [quote=nvteighen]The usual way to deal with this is to never use sizeof() into anything that is a pointer or an array to avoid possible undefined behaivor.[/QUOTE]Using the value of sizeof incorrectly might well lead to undefined behavior in other code (through buffer overflows, say), but the sizeof operator itself never directly causes undefined behavior.

---

### Post by dribeas on 2009-08-17
Very true, Lux Perpetua. Arrays are not pointers. The fact is that they are a special type in C (and has thus inherited the same properties in C++).

What makes arrays special is that they are treated differently from all other types when passed as function arguments. While all other types are passed by value (copied) into functions [*], arrays are not. Passing an array by value would be expensive both in the time to copy it and moreover in stack memory. Thus when the standard was developed they decided that arrays would 'decay' into pointers to the first element when passed to functions.

Most people will defend that they are in fact the same thing just because when used as function arguments they have the same meaning. That is, using the array syntax in function arguments yields exactly the same code as passing a plain pointer. 

In C, they are only different locally in the sense that Lux pointed out before, and you can have a simple macro to return the size of an array defined as:

```

#define ARRAY_SIZE( x ) ( (sizeof((x))/sizeof((x)[0]) )

```

If you move into C++, the difference is more notable. As in C++ you can pass function arguments by value or by reference you can use that to define a type safe method to calculate size:

```

template <typename T, std::size_t N>
inline std::size_t array_size( T (&)[N] ) {
   return N;
}

```

The compiler will deduce the template arguments and the result will be that N is matched to the number of elements in the array and returned. With current compilers the method will be converted into a constant at compile time with no runtime overhead (unless you explicitly request no inlining from the compiler and no optimizations). Note that the template will not accept a pointer, only arrays, and they are different types for the compiler.


[*] No, passing a pointer is not passing by reference, is just passing a pointer to the element by value. The pointer is copied. This is also a common misunderstanding with Java/C#, objects are not passed by reference, but rather references are passed by value. If you don't believe it try to implement swap as a function in Java.

---

### Post by ibuclaw on 2009-08-17
> **dribeas said:**
> 
```

#define ARRAY_SIZE( x ) ( (sizeof((x))/sizeof((x)[0]) )

```

That is probably the best way to go about it.

Although, bare in mind that only works for char[] types and not char* types.

---

### Post by matmatmat on 2009-08-18
The code is supposed to get the last letters of a string:
```

#include <stdio.h>

void end(char a[], int length)
{
    int retval;
    for(retval = 0; a[retval] != '\0'; retval++) {}	
	
	int endn = retval - length;	
	char en[length];	
	int i2;
	int b = 0;
	for(i2=0;i2<=retval;i2++){
		if (i2 >= endn){
			en[b]=a[i2];
			b++;
		}
	}
	printf(en);
	printf("\n");
}

int main(int argc, char** argv)
{
	char test[] = "TEST.TXT";
	end(test, 3); //should print TXT
	return 0;
}

```

---

### Post by nvteighen on 2009-08-18
Hm... You have taught me something new today. Thanks!

What seems to happen here is a difference in memory location...

```

char *a = "abc"; /* Is "abc" stored in .data section? Or even .code? */
char d[] = "def"; /* Undoubtfully, stored in stack */

```

Someone can enlighten me, please?

About sizeof()... When I said that it could lead to undefined behaivor, I wanted to mean that code using it could behaive undefinedly, not the operator itself. And that's why strlen() will never use that... Sorry if I wasn't clear enough.

---

### Post by dribeas on 2009-08-18
> **nvteighen said:**
> Hm... You have taught me something new today. Thanks!

What seems to happen here is a difference in memory location...

```

char *a = "abc"; /* Is "abc" stored in .data section? Or even .code? */
char d[] = "def"; /* Undoubtfully, stored in stack */

```

Someone can enlighten me, please?

The question is not where the data is allocated but the real type. An array has a given size that is known by the compiler (it had to reserve the space). The compiler knows how much space is reserved for it, and that is what sizeof() returns. When you have a pointer, the space reserved by the compiler for the variable is that of a native pointer type (32/64 bits), regardless of the memory that is pointed.

```

void f()
{
   char array[] = "Hi";
   char* p = array; // implicit cast
   assert( sizeof(array) != sizeof(p) );
}

```

The data is the same, but the variables are of different types. Another way of putting it is that given a type T, sizeof(T) returns the number of bytes that are required (without considering alignment or padding) in an struct to store an element of the type.

```

struct X {
   char array[10]; // 10 bytes are required to store 'array'
   char *p;        // 4/8 bytes are required to store 'p'
};

```

Maybe the problem is that the initialization syntax is misleading for arrays. The compiler is performing some extra work for you behind the scenes:

```

void f() {
   char a[] = "Hi";
// what the compiler processes (rough equivalence):
// char a[2]; memcpy( a, "Hi", 2 );

   char *p = a; 
}

```

---

### Post by nvteighen on 2009-08-18
Ok, thanks. :)

---

