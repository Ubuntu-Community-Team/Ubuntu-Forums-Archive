---
title: "C commandline options"
date: 2008-10-12
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-10-12
Is their a Linux C library for separating options (like "-aOtDsa") and other arguments? For a commandline utility

---

### Post by samjh on 2008-10-13
The standard method of getting command-line arguments is to use this definition for your main() function:
```
int main (int argc, char* argv[])
{
}
```int argc: the number of command-line arguments supplied.
char* argv[]: an array of C-strings containing the arguments themselves.

Take note that argc counts the program name too, and argv[] includes the program name as a command-line argument.

Example program:
```
#include <stdio.h>

int main(int argc, char* argv[])
{
	int i;

	for (i = 0; i < argc; i++) {
		printf("argv[%i] = %s\n", i, argv[i]);
	}

	return 0;
}
```
Save it as options.c and compile using gcc -o options options.c
Run the program with command-line arguments.  It will show you what argv[] contains.

Example execution:
```
linux-comp$ ./options hi there!
argv[0] = ./options
argv[1] = hi
argv[2] = there!
linux-comp$
```

Hope this helps. :)

---

### Post by Mr.Macdonald on 2008-10-13
maybe i should use the word parse,

like this
tar -cf ./test.tar ./folder

tar sees the -cf and knows to compress ./folder into ./test.tar

is their a library that allows me to pass argc and argv into it and it returns the options (-cf)

---

### Post by CptPicard on 2008-10-13
[http://www.gnu.org/software/libtool/manual/libc/Parsing-Program-Arguments.html#Parsing-Program-Arguments](http://www.gnu.org/software/libtool/manual/libc/Parsing-Program-Arguments.html#Parsing-Program-Arguments)

---

### Post by dwhitney67 on 2008-10-13
> **CptPicard said:**
> [http://www.gnu.org/software/libtool/manual/libc/Parsing-Program-Arguments.html#Parsing-Program-Arguments](http://www.gnu.org/software/libtool/manual/libc/Parsing-Program-Arguments.html#Parsing-Program-Arguments)

+1.

But it would've been easier to refer the OP to the manpage for getopt.  An example is provided.

---

### Post by Mr.Macdonald on 2008-10-13
wow thats perfect

I would have never guessed that argv_parse and getopt would parse my argv and get me the options!

now what is wrong with this in C

```

char * string, string2;
int i;

string = "hello"
string2 = malloc(20)
for (i=0;i<5;i++) string2[i] = string[i];

...

free(string);
free(string2);

```

---

### Post by dribeas on 2008-10-13
> **Mr.Macdonald said:**
> 
now what is wrong with this in C

```

char * string, string2;

```

That code is equivalent to:

```

char *string;
char string2;

```

---

### Post by snova on 2008-10-13
No NUL terminator? Change 5 to 6.

---

### Post by dwhitney67 on 2008-10-13
When declaring a variable, initialize it at the same time.  I understand you are programming in C, however in C++, when declaring a char * variable to equal a string literal, current standards require you to implicitly declare the variable as a const.  You should get into the habit of doing the same in C.

Thus,
[PHP]
const char * string  = "hello";
char *       string2 = strdup( string );   // duplicate the string; allocates memory

...

free( string2 );

...[/PHP]

P.S. Also note that it is not possible to change the contents of a string literal.  It is fixed in memory once defined.  Thus, with the code above, the following is _not_ possible for obvious reasons; but even if 'string' was declared non-const it would not be possible:
[PHP]string[0] = 'H';[/PHP]

---

