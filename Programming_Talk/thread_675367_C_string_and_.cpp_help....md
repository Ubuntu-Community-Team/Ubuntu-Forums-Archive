---
title: "C string and .cpp help..."
date: 2008-01-22
forum: Programming Talk
---

### Post by crashovaride on 2008-01-22
I'm frustrated, but keeping my cool. I've been searching for this solution for the last past 2.3 weeks, and to no signs of help. However, I'm still coding on with my application in the sections i know how to write. 

I'm searching for two things, and i can't seem to find the proper solution for any. My first approach is that i'm trying to add additional text to a string. For example we have the following code:

[PHP]#include <stdio.h>
#include <string.h>

int main()
{
         char *apache;
         apache="this is some data";
         
         printf("please wait while we add additional information.\n");
         ...
         return 0;
}[/PHP]

I have tried apache = apache & "new data", apache = apache + "new data" apache .= "data", apache = apache ++ "data"; etc. Nothing has worked. I even tried strcpy(apache2, "new data"); and it's failing to work. Maybe i'm doing something wrong? Please someone help me. 

In addition to which. I'm trying to break my application down smaller so it's less confusing for a person to man and operate if they download and want to change code. I've tried to make separate modules for apache, ssh, grub, etc. And, place them into .cpp files. When i call them #include apache.cpp and attempt to compile, i get compile errors. Is there an alternate way to do this? Please let me know (im in no way searching for people to do my work for me. i just want to understand this language in more detail). 

Thank you.

---

### Post by Wybiral on 2008-01-22
[strcat]("http://cppreference.com/stdstring/strcat.html") is the way to go... I don't want to give you too many answers, but I will say this: pay attention to the compiler warnings and errors when you use it.

After you give them a look, post back and explain what you don't understand (if you don't understand it).

EDIT:

Why is this in a ".cpp" file, this is definitely C, not C++...

---

### Post by melopsittacus on 2008-01-22
Hi! What complier errors do you get when you use include?

Anyway, you should not include a .cpp or .c file, just a .h (header) file. Header files hold the declarations of your fuctions and should be included both in the .cpp file that implements those functions and in the .cpp files that wil use thos functions.

---

### Post by dwhitney67 on 2008-01-22
Be wary of strcat().  Yes it will serve the purpose of concatenating two strings, however the destination buffer needs to be sized appropriately to handle the length of the new string.

If you are using a char pointer to declare your initial string, use malloc() to assign space for it, then realloc() to adjust the size of the string when/if more space is required to add more to the string.

---

### Post by crashovaride on 2008-01-22
For this sshd_configs = sshd_configs ++ "new data " we get 

securitysleuth.c: In function ‘ssh_config’:
securitysleuth.c:304: error: expected ‘;’ before string constant

Which i had also added the ; the end of the statement. And, it continues to error. 

------

sshd_configs .= sshd_configs "new data "
with and without the ; produces the error:
securitysleuth.c: In function ‘ssh_config’:
securitysleuth.c:304: error: expected identifier before ‘=’ token
-------

sshd_configs == sshd_configs "new data "
produces...
securitysleuth.c: In function ‘ssh_config’:
securitysleuth.c:304: error: expected ‘;’ before string constant

--------
with double && in place of = we get
securitysleuth.c: In function ‘ssh_config’:
securitysleuth.c:304: error: invalid operands to binary &
securitysleuth.c:304: error: expected ‘;’ before string constant
this is also without the ;

I'm dead in the water here...

---

### Post by dwhitney67 on 2008-01-22
What are you writing, a C program or a C++ program.  Some of those who replied previous to me were also confused.

If you are writing a C++ program, then declare an std::string.  For instance:

[PHP]std::string str( "Hello" );

str += " World";[/PHP]

If you are writing a C program:

[PHP]char *str = malloc( 6 );
strncpy( str, "Hello", 6 );
str = realloc( str, 12 );
strncat( str, " World", 6 );
[/PHP]

---

### Post by Wybiral on 2008-01-22
> **crashovaride said:**
> I'm dead in the water here...

No, you just don't seem to understand what a pointer is. There's no reason why adding a character array to a character pointer should do what you want. If that statement doesn't make any sense to you, then do some research on pointers until you grasp them. They can be tricky at first, but once you get them, you will understand what I'm saying here.

---

### Post by hod139 on 2008-01-22
> **dwhitney67 said:**
> 

]If you are writing a C program:

[php]char *str = malloc( 6 );
strncpy( str, "Hello", 6 );
str = realloc( str, 12 );
strncat( str, " World", 6 );
[/php]

Be careful with strncpy, it too can be evil.  strncpy does not null terminate the destination buffer, so if the source string was larger than the allocated space, strncpy will leave you with a malformed string.  It is good practice to always null terminate the destination string, so if the input is ever too large you at least still have a well formed string.

```

char *str = malloc( 6 );
strncpy( str, "HelloWorld", 6 ); // **BAD:** str is now malformed
str[5]='\0'; // fixed!!!!

```Also, when the src string is smaller than the destination, strncpy will pad the destination buffer with zeros, which is often times an unnecessary waste.

---

### Post by dwhitney67 on 2008-01-22
Hod139, while I do agree that one must be careful when using strncpy(), or its more evil sibling, strcpy(), one must accept certain risks when writing software.  One could easily place the terminating null character in the wrong position too!  For instance, using your example:
[PHP]
str[15] = '\0';   // oops, should be a 5, not a 15[/PHP]

Now you may think that nobody would make a silly mistake as shown above, but I know some programmers out there that are sheer clumsy when it comes to paying attention to detail.  The mistake above could easily clobber other values sitting in memory.

Anyhow, we all must be careful programmers.  We don't want our "greeting to the world" to be corrupted.

---

### Post by crashovaride on 2008-01-22
When i use the .h i get the following error(s): 

securitysleuth.c:70:21: error: apache.h: No such file or directory

---

### Post by dwhitney67 on 2008-01-22
Do you know where that header file exists?  If so, specify that path with the -I option when you compile.  For example:

```
$ g++ -I/path/to/header myprog.cpp
```

---

### Post by crashovaride on 2008-01-22
Well, this is an external source file that i would like to reference. for example apache.cpp, apache.c or apache.h i'm not sure how i would go about doing this and linking it. I keep getting errors.

---

### Post by crashovaride on 2008-01-28
> **Wybiral said:**
> No, you just don't seem to understand what a pointer is. There's no reason why adding a character array to a character pointer should do what you want. If that statement doesn't make any sense to you, then do some research on pointers until you grasp them. They can be tricky at first, but once you get them, you will understand what I'm saying here.

I'm almost there using your example. I'm getting errors but i'm trying to work through the example you sent on strcat. Thanks for the help (and this goes for everyone as well.)

---

### Post by stroyan on 2008-01-28
The conventional way to break up code in a moderate sized program is to have several separately compiled .c source files that are linked together to make one executable.  Each .c file has a matching .h file that defines the functions and global variables that can be accessed by code in other .c files.  You can include header files in the local directory by using '#include "a.h"' instead of '#include <a.h>'.  The quote style looks in local directories as well as the system header directories.
This arrangement allows changes to be made to one file without recompiling everything.
Here is an example of a main program that uses functions from two other source files.  It is also possible for files like a.c and b.c to include the header files for eachother and call functions from eachother.
The 'Makefile' declares what needs to be done to build or rebuild.
The make command is used to keep track or which files need to be recompiled when certain files are changed.  The example program is built by running 'make'.  (Be carefull with indentation of makefiles.  The indented lines are the commands to run.  They _must_ start with a tab character to be treated as a command.  Spaces will not work.)
```
::::::::::::::
a.c
::::::::::::::
int A(int p)
{
        return p+2;
}
::::::::::::::
a.h
::::::::::::::
/* declare functions in a.c */
int A(int p);
::::::::::::::
b.c
::::::::::::::
int B(int p)
{
        return p+8;
}
::::::::::::::
b.h
::::::::::::::
/* declare functions in b.c */
int B(int p);
::::::::::::::
main.c
::::::::::::::
#include "a.h"
#include "b.h"

int main(int argc, char *argv[])
{
        A(2);
        B(3);
        return 0;
}
::::::::::::::
Makefile
::::::::::::::
example: main.o a.o b.o
        cc -o example main.o a.o b.o

a.o: a.c
        cc -c a.c

b.o: b.c
        cc -c b.c

main.o: main.c a.h b.h
        cc -c main.c

clean:
        rm -f a.o b.o main.o example

```

---

### Post by crashovaride on 2008-02-01
stroyan,

      Thank you for the example, i'm working using my own implementation of it from your example. Thank you so much.

---

