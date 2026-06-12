---
title: "Warning message from G++, not GCC - why?"
date: 2009-02-25
forum: Programming Talk
---

### Post by Krupski on 2009-02-25
Hi all,

I just got done writing a little utility and when I compile it with GCC, I get no warnings (btw, -Wextra is on). But, with G++ I get this warning:

```

stripcr.c:30: warning: deprecated conversion from string constant to ‘char*’

```

...and here is the "offending" line:

```

    strcpy(buffer, bname(argv[0], "/"));

```

"bname" is a small function that I wrote - it returns the basename of a string. For example, "/usr/local/sbin/myprogram" would be returned as "myprogram" (i.e. my function is a clone of the "basename() function).

Here's bname:

```

char *bname(char *p0, char *delim)
{
    char tmp[MAX];
    char *p1;
    char *p2;

    strcpy(tmp, p0); // copy to avoid modifying input

    p2 = strtok(tmp, delim); // initial pointer

    while(p2 != NULL) { // while current pointer != null
        p1 = p2; // copy current to previous
        p2 = strtok(NULL, delim); // point to next token
    }

    return p1; // p1 = pointer to last token
}

```

Anyone know why I get the warning with G++ and not with GCC?

By the way, the program DOES work... all I get is a warning.

Thanks!

-- Roger

---

### Post by dwhitney67 on 2009-02-25
You need to get into the habit of specifying your char* declarations with a 'const' when appropriate.

For instance, in your bname() function, you have a comment indicating that you want to avoid changing the input parameter.  Well, if you had declared that input parameter as 'const char*', then you would not have to worry about accidentally overwriting it.

Of course, the stricter your code, the more compilation warnings you will get.  And what g++ is telling you is that bname() is returning a non-const char*.  Change the signature of your function to be:
```

const char* bname(const char* p0, const char* delim);

```
Then all should be well -- well almost; other warnings may crop up.


P.S.
Some additional help...
```

#include <string.h>
#include <stdlib.h>
#include <stdio.h>

const char* bname(const char* str, const char* delim)
{
  char* token     = strdup(str);
  char* lastToken = 0;
  char* tmp       = token;

  token = strtok(token, delim);

  while (token)
  {
    lastToken = token;
    token     = strtok(0, delim);
  }

  free(tmp);

  return (const char*) lastToken;
}

int main()
{
  const char* str    = "|FEE|FI|FO|FUM|";
  const char* delim  = "|";
  const char* result = bname(str, delim);

  printf("%s\n", (result ? result : "null"));

  return 0;
}

```

---

### Post by DougB1958 on 2009-02-25
GCC is a broad spectrum compiler, it compiles a number of related languages, using a source file's extension to decide what language the file is written in. With a ".c" extension, "stripcr.c" will be compiled as a C (not C++) program; in C, a quoted sequence of characters compiles to a pointer to a block of memory containing the characters -- i.e., the "/" in your program compiles to a char*, just like bname expects.

G++, on the other hand, only compiles C++, and assumes that any source file it is given contains C++. In C++, a quoted string of characters compiles into a C++ string object, **not** a pointer to a character. Thus the compiler generates one type for the "/" parameter to bname, sees that bname expects a different but similar type, and tries to coerce the actual parameter to the right type -- but the necessary coercion is now deprecated.

---

### Post by lloyd_b on 2009-02-25
Please remember that G++ invokes C++ rules, which can generate warnings on perfectly valid C code.  It apparently doesn't like converting the string literals "/" to a char pointer - not sure why.

BTW: Have you looked at the rindex() function?  I think it would handle most of the work of bname(), and it's designed to use a delimiter character (as opposed to a token string like strtok()).

Lloyd B.

---

### Post by soltanis on 2009-02-25
DougB1958 is correct.

C++ has stricter typing, and treats strings differently than C.

---

### Post by monkeyking on 2009-02-25
> **dwhitney67 said:**
> You need to get into the habit of specifying your char* declarations with a 'const' when appropriate.


Yes, write your char* with const.
But it's generally a good idea to use const whenever you are certain, that the values won't be changed. This will be a lifesaver on larger programs.

[http://www.parashift.com/c++-faq-lite/const-correctness.html](http://www.parashift.com/c++-faq-lite/const-correctness.html)

---

### Post by Krupski on 2009-02-25
Thank you to **dwhitney67**, **DougB1958**, **lloyd_b**, **soltanis** and **monkeyking**.

That makes perfect sense (and it worked too!) :)

Thanks again for the quick replies and the great help!

-- Roger

---

### Post by movieman on 2009-02-26
> **DougB1958 said:**
> In C++, a quoted string of characters compiles into a C++ string object, **not** a pointer to a character.

'string' is part of the standard C++ libraries, not the C++ language.

I'm 99% certain that a string literal is simply an array of chars like C, but they're const chars and C++ will only allow you to take a char * pointer to a const string literal without a cast because it's required for backwards compatibility with C... hence the warning, because that behaviour is likely to go away in future.

C string literals, on the other hand, may or may not be writable depending on the compiler; I think pretty much all Unix compilers put them in a read-only segment of the program so you'll probably get a segmentation fault if you try to write to one.

---

### Post by DougB1958 on 2009-02-28
> **movieman said:**
> 
I'm 99% certain that a string literal is simply an array of chars like C, but they're const chars and C++ will only allow you to take a char * pointer to a const string literal without a cast because it's required for backwards compatibility with C... hence the warning, because that behaviour is likely to go away in future.

You're right. To settle this in my own mind I tried compiling the following, which is basically just a bunch of declarations that should provoke errors from G++ according to how it interprets quoted character sequences:

[PHP]#include <string>
using std::string;


int main( int argc, char* argv[] ) {

	const char* ptr1 = "abc";
	char* ptr2 = "def";

	string s1 = "ghi";
	string s2 = "jkl" + "mno";
}[/PHP]

and...

```
doug@ubuntu:~/DevTest$ g++ -c string.cpp
string.cpp: In function ‘int main(int, char**)’:
string.cpp:13: warning: deprecated conversion from string constant to ‘char*’
string.cpp:16: error: invalid operands of types ‘const char [4]’ and ‘const char [4]’ to binary ‘operator+’
```

The second error message (re line 16) is the smoking gun, it pretty explicitly says the two quoted sequences are (pointers to) char arrays.

Thanks for straightening me out.

---

