---
title: "c strings and pointers problem.."
date: 2007-08-03
forum: Programming Talk
---

### Post by rbprogrammer on 2007-08-03
so i have written this code:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

unsigned long cstrlength(char const * const str)
{
	unsigned long length = 0;
	if( str != NULL )
		while( str[length] != '\0' )
			length++;
	return length;
}
char const * cstrscan(char *str, char endchar)
{
	if( str != NULL )
		free( str );
	char c = 0;
	unsigned long length = 1;
	str = ( char* )malloc( length*sizeof(char*) );
	if( str == NULL )
		return NULL;
	str[0] = '\0';
	while( 1 )
	{
		c = fgetc( stdin );
		if( c == endchar )
			break;
		else
		{
			str = ( char* )realloc(str, ((length+1)*sizeof(char*)));
			if( str == NULL )
				return NULL;
			str[length-1] = c;
			str[length] = '\0';
		}
		length++;
	}
	return str;
}
char const * cstrcopy(char* dest,  char const * src)
{
	if( src == dest )
		return dest;
	if( dest != NULL )
		free( dest );
	unsigned long length = cstrlength(src);
	dest = ( char* )malloc( (length+1)*sizeof(char*) );
	if( dest == NULL )
	{
		puts("Error allocating memory!\n");
		return NULL;
	}
	char *p = dest;
	char const *q = src;
	if( length != 0 )
	{
printf("length == %lu\n", cstrlength(src));		//debugging purposes only
		unsigned long ct = 0;
		for(ct=0; ct<length; ct++,p++,q++)
			*p = *q;
printf("length == %lu\n", cstrlength(src));		//debugging purposes only
	}
	else
		printf("length==0\n");
	*p = '\0';
printf("dest == %s\n", dest);		//debugging purposes only
	return dest;
}

int main(int argc, char *argv[])
{
	char *str = ( char* )malloc( 1*sizeof(char*) );
	char *buffer = ( char* )malloc( 1*sizeof(char*) );//"one two three four five six seven eight";

	cstrscan(buffer, '\n');
	cstrcopy(str, buffer);

	printf("\tstr: %8lu => %s\n", cstrlength(str), str);
	printf("\tbuffer1: %4lu => %s\n", cstrlength(buffer), buffer);

	printf("\n");

	//free(str);
	free(buffer);

	return 0;
}

```
then when i execute [FONT="Courier New"]gcc[/FONT], i get this error:
```

$ gcc -Wall test.c -o test
$ ./test
one two
length == 7
length == 7
dest == one two
        str:        0 =>
        buffer1:    7 => one two

```
why does [FONT="Courier New"]str[/FONT] not point to the address that [FONT="Courier New"]dest[/FONT] points to in [FONT="Courier New"]cstrcopy()[/FONT]??

answering this question would probably answer my next question that is why do i have to comment out the [FONT="Courier New"]free(str)[/FONT] at the end of my [FONT="Courier New"]main()[/FONT]??  when i uncomment it out, i get a huge error called a backtrace and a memory map or something like that..

****NOTE****
with all that said, i would now like to explain what i'm doing.  i know there are people that are going to say that all this has been done and that i might be wasting my time reinventing the wheel.  but the thing is that i like to program and learn everything about it.  and i see that the best way to do this is to write your own code.  then when i have programming projects for school, the professors love it when you go above the assignment.  and up to now (going into my third year of college) we have not gotten into most of this stuff yet.  so if i use [FONT="Courier New"]strlen(), strcpy(), strcat()[/FONT] when it was not covered in class, the professor might get suspicious.  but if i make my own function using pointers that we already learned, then its all good.

---

### Post by noof on 2007-08-03
I also like to write own things, but you'll learn what to write on your own and what to just use after a while :)

Anyways, the first problem is that you malloc a char* that can store one char*. This is probably not what you mean I think. On a 32-bit system a char* (or any pointer) is 4 bytes (8 in a 64-bit OS), which means your char* is a pointer to a memory to store 4 bytes.

The error is that you should treat pointers as ordinary values. This is what you're doing:
```
void test(int a){ 
  a++;
}
void main() {
  int b = 1; 
  test(b); 
}
```

and expect b to be 2 after the call to test. But it'll be 1 since test only modifies its local copy of the value. The same thing happens to your pointers, the function modifies the local copy of the pointer. This is the reason that "free(str);" generates an error, you have already freed it in the copy function. This leaves you with two options:
1) Use pointer to pointer:
```
void cpy(char** dest, const char* src) {
  if( *dest != NULL ) free ( *dest );
  *dest = malloc( strlen(src)+1 );
  strcpy( *dest, src );
}
void main() {
  char* test = malloc(17);
  cpy( test, "hello there" );
  free( test );
}
```

If you're confused by double pointers you should google some more for it. This is btw a horrible solution :)

2) This is the way most c-functions work:
```
void cpy(char* dest, int max_size, const char* src) {
  int len = min( max_size-1, strlen(src)-1 );
  // copy 'len' characters from src to dest
}
void main() {
  char* test = malloc(17);
  cpy( test, 17, "hello there" );
  free( test );
}
```

This is much better, trust me :) You do not want to free other functions pointers every now and then.

Hope this gives you some clues on where to continue.

---

### Post by rbprogrammer on 2007-08-03
for some reason i though when i do a [FONT="Courier New"]sizeof(char*)[/FONT] it was going to dereference the pointer..  doing a little test:
```

printf("%i\n", sizeof(char));
printf("%i\n", sizeof(char*));

```
i see that it obviously was not, i feel so dumb now :) ..

so i changed all the [FONT="Courier New"]sizeof(char*)[/FONT] to [FONT="Courier New"]sizeof(char)[/FONT] and it cleared up the error of [FONT="Courier New"]str[/FONT] not pointing to what i wanted.

here is my new code:
```


#include <stdio.h>
#include <stdlib.h>
unsigned long cstrlength(char const * const str)
{
	unsigned long length = 0;
	if( str != NULL )
		while( str[length] != '\0' )
			length++;
	return length;
}
char const * cstrscan(char *str, char endchar)
{
	if( str != NULL )
		free( str );
	char c = 0;
	unsigned long length = 1;
	str = ( char* )malloc( length*sizeof(char) );
	if( str == NULL )
		return NULL;
	str[0] = '\0';
	while( 1 )
	{
		c = fgetc( stdin );
		if( c == endchar )
			break;
		else
		{
			str = ( char* )realloc(str, ((length+1)*sizeof(char)));
			if( str == NULL )
				return NULL;
			str[length-1] = c;
			str[length] = '\0';
		}
		length++;
	}
	return str;
}
char const * cstrcopy(char* dest,  char const * src)
{
	if( src == dest )
		return dest;
	if( dest != NULL )
		free( dest );
	unsigned long length = cstrlength(src);
	dest = ( char* )malloc( (length+1)*sizeof(char) );
	if( dest == NULL )
	{
		puts("Error allocating memory!\n");
		return NULL;
	}
	char *p = dest;
	char const *q = src;
	if( length != 0 )
	{
		unsigned long ct = 0;
		for(ct=0; ct<length; ct++,p++,q++)
			*p = *q;
	}
	else
		printf("length==0\n");
	*p = '\0';
	return dest;
}

int main(int argc, char *argv[])
{
	char *str = ( char* )malloc( 1*sizeof(char) );
	char *buffer = ( char* )malloc( 1*sizeof(char) );//"one two three four five six seven eight";

	cstrscan(buffer, '\n');
	cstrcopy(str, buffer);

	printf("\tstr: %8lu => %s\n", cstrlength(str), str);
	printf("\tbuffer1: %4lu => %s\n", cstrlength(buffer), buffer);

	printf("\n");

	//free(str);
	free(buffer);

	return 0;
}

```

now i tried two different inputs and i get this error but i dont understand why i got an error for the longer string: (italics is input)
```

$ gcc -Wall test.c -o test
$ ./test
*one two*
        str:        7 => one two
        buffer1:    7 => one two

$ ./test
*one two three four five*
        str:        0 =>
        buffer1:   23 => one two three four five

*** glibc detected *** ./test: double free or corruption (fasttop): 0x0804a008 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e1e7cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e21e30]
./test[0x804873a]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7dccebc]
./test[0x8048461]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:05 98527      /home/mike/Desktop/pointers/test
08049000-0804a000 rw-p 00000000 08:05 98527      /home/mike/Desktop/pointers/test
0804a000-0806b000 rw-p 0804a000 00:00 0          [heap]
b7c00000-b7c21000 rw-p b7c00000 00:00 0
b7c21000-b7d00000 ---p b7c21000 00:00 0
b7db6000-b7db7000 rw-p b7db6000 00:00 0
b7db7000-b7ef2000 r-xp 00000000 08:01 762815     /lib/tls/i686/cmov/libc-2.5.so
b7ef2000-b7ef3000 r--p 0013b000 08:01 762815     /lib/tls/i686/cmov/libc-2.5.so
b7ef3000-b7ef5000 rw-p 0013c000 08:01 762815     /lib/tls/i686/cmov/libc-2.5.so
b7ef5000-b7ef8000 rw-p b7ef5000 00:00 0
b7efc000-b7f07000 r-xp 00000000 08:01 759582     /lib/libgcc_s.so.1
b7f07000-b7f08000 rw-p 0000a000 08:01 759582     /lib/libgcc_s.so.1
b7f08000-b7f0c000 rw-p b7f08000 00:00 0
b7f0c000-b7f25000 r-xp 00000000 08:01 759541     /lib/ld-2.5.so
b7f25000-b7f27000 rw-p 00019000 08:01 759541     /lib/ld-2.5.so
bffe6000-bfffc000 rw-p bffe6000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

---

### Post by Wybiral on 2007-08-03
I haven't looked too closely...

But your problem is that you aren't changing the pointer being sent to cstrcopy.

You have the function allocating memory, but you're not changing the original pointer.

Try using a:

char const * cstrcopy(char** dest,  char const * src)

Then address 'dest' by dereferencing it '(*dest)'

Don't forget to pass by reference: cstrcopy(&dest, src). It's the only way to can let the function change the address in "str" (not the data at the address, but the address the pointer stores).

C's strcpy function doesn't work this way though, it assumes the destination is already big enough and simply copies data to it. But, if you want yours to work this way it will have to change the pointer being sent as a parameter if you're going to change the address.

Right now, you may as well just use "dest" as a local function variable :)

This explains your "free" problem too since you are freeing the data in your function, then you're not 'malloc'ing (you're 'malloc'ing "dest" but "str" doesn't get changed). You also have a memory leak since "dest" is never freed.

You need to set "str" to the address that your function set's "dest" to.


Here's what I mean by using a pointer to the char pointer (char **src) so that you can change the address that "str" holds.

EDIT:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

unsigned long cstrlength(char const * const str)
{
	unsigned long length = 0;
	if( str != NULL )
		while( str[length] != '\0' )
			length++;
	return length;
}
char const * cstrscan(char *str, char endchar)
{
	if( str != NULL )
		free( str );
	char c = 0;
	unsigned long length = 1;
	str = ( char* )malloc( length*sizeof(char*) );
	if( str == NULL )
		return NULL;
	str[0] = '\0';
	while( 1 )
	{
		c = fgetc( stdin );
		if( c == endchar )
			break;
		else
		{
			str = ( char* )realloc(str, ((length+1)*sizeof(char*)));
			if( str == NULL )
				return NULL;
			str[length-1] = c;
			str[length] = '\0';
		}
		length++;
	}
	return str;
}
char const * cstrcopy(char** dest,  char const * src)
{
	if( src == *dest )
		return *dest;
	if( *dest != NULL )
		free( *dest );
	unsigned long length = cstrlength(src);
	*dest = ( char* )malloc( (length+1)*sizeof(char*) );
	if( *dest == NULL )
	{
		puts("Error allocating memory!\n");
		return NULL;
	}
	char *p = *dest;
	char const *q = src;
	if( length != 0 )
	{
printf("length == %lu\n", cstrlength(src));		//debugging purposes only
		unsigned long ct = 0;
		for(ct=0; ct<length; ct++,p++,q++)
			*p = *q;
printf("length == %lu\n", cstrlength(src));		//debugging purposes only
	}
	else
		printf("length==0\n");
	*p = '\0';
printf("dest == %s\n", *dest);		//debugging purposes only
	return *dest;
}

int main(int argc, char *argv[])
{
	char *str = NULL;
	char *buffer = ( char* )malloc( 1*sizeof(char*) );

	cstrscan(buffer, '\n');
	cstrcopy(&str, buffer);

	printf("\tstr: %8lu => %s\n", cstrlength(str), str);
	printf("\tbuffer1: %4lu => %s\n", cstrlength(buffer), buffer);

	printf("\n");

    free(str);
	free(buffer);

	return 0;
}

```

Classic case of the mistaken identity of the pointer. Pointers are nothing but addresses... You passing the address to a function. It's like this:

```

void example(int x)
{
    x = 5;
}

```

'int' is no different then 'char *' except for the fact that it isn't an address.

EDIT:

Just realized the second poster made a similar comment :)

---

### Post by slavik on 2007-08-04
> **Wybiral said:**
> I haven't looked too closely...

But your problem is that you aren't changing the pointer being sent to cstrcopy.

You have the function allocating memory, but you're not changing the original pointer.

Try using a:

char const * cstrcopy(char** dest,  char const * src)

Then address 'dest' by dereferencing it '(*dest)'

Don't forget to pass by reference: cstrcopy(&dest, src). It's the only way to can let the function change the address in "str" (not the data at the address, but the address the pointer stores).

C's strcpy function doesn't work this way though, it assumes the destination is already big enough and simply copies data to it. But, if you want yours to work this way it will have to change the pointer being sent as a parameter if you're going to change the address.

Right now, you may as well just use "dest" as a local function variable :)

This explains your "free" problem too since you are freeing the data in your function, then you're not 'malloc'ing (you're 'malloc'ing "dest" but "str" doesn't get changed). You also have a memory leak since "dest" is never freed.

You need to set "str" to the address that your function set's "dest" to.


Here's what I mean by using a pointer to the char pointer (char **src) so that you can change the address that "str" holds.

EDIT:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

unsigned long cstrlength(char const * const str)
{
	unsigned long length = 0;
	if( str != NULL )
		while( str[length] != '\0' )
			length++;
	return length;
}
char const * cstrscan(char *str, char endchar)
{
	if( str != NULL )
		free( str );
	char c = 0;
	unsigned long length = 1;
	str = ( char* )malloc( length*sizeof(char*) );
	if( str == NULL )
		return NULL;
	str[0] = '\0';
	while( 1 )
	{
		c = fgetc( stdin );
		if( c == endchar )
			break;
		else
		{
			str = ( char* )realloc(str, ((length+1)*sizeof(char*)));
			if( str == NULL )
				return NULL;
			str[length-1] = c;
			str[length] = '\0';
		}
		length++;
	}
	return str;
}
char const * cstrcopy(char** dest,  char const * src)
{
	if( src == *dest )
		return *dest;
	if( *dest != NULL )
		free( *dest );
	unsigned long length = cstrlength(src);
	*dest = ( char* )malloc( (length+1)*sizeof(char*) );
	if( *dest == NULL )
	{
		puts("Error allocating memory!\n");
		return NULL;
	}
	char *p = *dest;
	char const *q = src;
	if( length != 0 )
	{
printf("length == %lu\n", cstrlength(src));		//debugging purposes only
		unsigned long ct = 0;
		for(ct=0; ct<length; ct++,p++,q++)
			*p = *q;
printf("length == %lu\n", cstrlength(src));		//debugging purposes only
	}
	else
		printf("length==0\n");
	*p = '\0';
printf("dest == %s\n", *dest);		//debugging purposes only
	return *dest;
}

int main(int argc, char *argv[])
{
	char *str = NULL;
	char *buffer = ( char* )malloc( 1*sizeof(char*) );

	cstrscan(buffer, '\n');
	cstrcopy(&str, buffer);

	printf("\tstr: %8lu => %s\n", cstrlength(str), str);
	printf("\tbuffer1: %4lu => %s\n", cstrlength(buffer), buffer);

	printf("\n");

    free(str);
	free(buffer);

	return 0;
}

```

Classic case of the mistaken identity of the pointer. Pointers are nothing but addresses... You passing the address to a function. It's like this:

```

void example(int x)
{
    x = 5;
}

```

'int' is no different then 'char *' except for the fact that it isn't an address.

EDIT:

Just realized the second poster made a similar comment :)
const, reference??? since when are those in C??? :)

---

### Post by hod139 on 2007-08-04
> **slavik said:**
> const, reference??? since when are those in C??? :)
const has been around since the C99 standard.  
As for reference, don't think the C++ reference operator.  Wybrial was talking about pass-by-reference, which he accomplished by passing the address of the pointer.  C++ cleans up the syntax of pass-by-reference with syntactic sugar.  You no longer have to pass pointers to pointers to accomplish pass-by-reference.

---

### Post by slavik on 2007-08-04
learn something new everyday. thanks. ^^

---

### Post by rbprogrammer on 2007-08-05
instead of declaring the function as:
```
char const * cstrcopy(char** dest, char const * src)
```

why cant i do this in C? but C++ its valid..
```
char const * cstrcopy(char* &dest, char const * src)
```

because for the first example, i would have to remember to dereference the pointer every time i call the function like:
```
cstrcopy(*destPtr, srcPtr)
```

also, what happens if i ever need to create a [FONT="Courier New"]char**[/FONT] variable??  i think it would then get even more complicated..

or should i declare it as [FONT="Courier New"]char* var[][/FONT]??

---

### Post by Wybiral on 2007-08-05
> **rbprogrammer said:**
> instead of declaring the function as:
```
char const * cstrcopy(char** dest, char const * src)
```

why cant i do this in C? but C++ its valid..
```
char const * cstrcopy(char* &dest, char const * src)
```

because for the first example, i would have to remember to dereference the pointer every time i call the function like:
```
cstrcopy(*destPtr, srcPtr)
```

also, what happens if i ever need to create a [FONT="Courier New"]char**[/FONT] variable??  i think it would then get even more complicated..

or should i declare it as [FONT="Courier New"]char* var[][/FONT]??

C just doesn't have the C++ reference operator in function parameters.

In C, passing with '&somevariable' is the only way to pass the address of the variable itself. It's kind of sad, but it's true.

Btw, 'var[]' and '*var' are really the same thing.

---

### Post by rbprogrammer on 2007-08-06
> **Wybiral said:**
> 
Btw, 'var[]' and '*var' are really the same thing.


so then threre is absolutely no difference other than looks for the following:
```

char** ptr;
char* ptr[ someSize ];

```
??

---

### Post by Mr. C. on 2007-08-06
> **rbprogrammer said:**
> so then threre is absolutely no difference other than looks for the following:
```

char** ptr;
char* ptr[ someSize ];

```
??

Not quite.  someSize must be known at compile time, and space for someSize x sizeof char * bytes are reserved and allocated.  The char** reference only allocates a single pointer.

A char *ptr[] would be an incomplete type, which can be used for forward references, or as the type of a function parameter, where it is simply considered and converted to a pointer.

MrC

---

### Post by Wybiral on 2007-08-07
> **rbprogrammer said:**
> so then threre is absolutely no difference other than looks for the following:
```

char** ptr;
char* ptr[ someSize ];

```
??

When they are used as function parameters "var[]" and "*var" are the same thing.

When you are declaring the data itself, obviously it will make a difference.

This is why you see some people use "int main(int argc, char **argv)" and some people use "int main(int argc, char *argv[])"

It's the same thing.

---

