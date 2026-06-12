---
title: "[SOLVED] Compiling and linking multiple files in C"
date: 2008-10-20
forum: Programming Talk
---

### Post by swappo1 on 2008-10-20
Hello,

I want to compile and link two files in C.  I am using Schaum's Programming With C which uses Boreland C in windows.  I am not sure how to apply this to compile and link multiple files within linux.  Here is what I have:

file1.c
[PHP]#include <stdio.h>		// saved as file1.c

extern void output(void);		//function prototype

main()
{
	output();
}
[/PHP]

file2.c
[PHP]extern void output(void)		// external function definition
{								// saved as file2.c
	printf("Hello, there");
	return;
}[/PHP]

I tried compiling and linking the two files using:
> scott@scott-laptop:~$ gcc -o file3 file1.c file2.c


This is what I got in response:
> file2.c: In function ‘output’:
file2.c:3: warning: incompatible implicit declaration of built-in function ‘printf’


I am not really sure what I am doing here and I couldn't find any tutorials on how to link multiple files.  How would I link these two files?

Thanks

---

### Post by WW on 2008-10-20
In file2.c, you need **#include <stdio.h>**.

Also, in file2.c, don't use the **extern** keyword in the definition of the funcion.

---

### Post by swappo1 on 2008-10-20
Ok, I included **#include<stdio.h>** in the second file and it works now.  I'm not sure why I shouldn't use extern in the definition of the function.  Can you explain this?

Thanks

---

### Post by swappo1 on 2008-10-20
One more thing.  Is there another way of doing this?  Like creating file1.c with a reference to compile and link file2 from within file1.c.  I would then only have to compile and link file1.c.  Not sure if this makes sense or not.  It just seems that with a large number of files, things can get confusing and disorganized.

---

### Post by namegame on 2008-10-20
> **swappo1 said:**
> One more thing.  Is there another way of doing this?  Like creating file1.c with a reference to compile and link file2 from within file1.c.  I would then only have to compile and link file1.c.  Not sure if this makes sense or not.  It just seems that with a large number of files, things can get confusing and disorganized.

When I code programs with multiple header files, source files, etc, I prefer to create a makefile. It streamlines the compilation process.

---

### Post by swappo1 on 2008-10-20
> When I code programs with multiple header files, source files, etc, I prefer to create a makefile. It streamlines the compilation process.

How do I create a makefile?  Is the makefile called from within the C program?

---

### Post by nvteighen on 2008-10-20
> **swappo1 said:**
> Ok, I included **#include<stdio.h>** in the second file and it works now.  I'm not sure why I shouldn't use extern in the definition of the function.  Can you explain this?

Just because extern means something else. It's used when you have a global variable in a module A.c and you want to access it from module B.c, so you write **extern var_name;** in the B.c file.

But globals are considered bad practice...

When you compile a program from multiple files, it's the linker's job to find where the functions are defined among the source or object files you provide the compiler. But, the best is to also use header files where you just include the declarations (aka prototypes) of all functions you want to make publicly available (those you want to be private should not be included on the header and also marked as **static** in the source file).

> **swappo1 said:**
> One more thing.  Is there another way of doing this?  Like creating file1.c with a reference to compile and link file2 from within file1.c.  I would then only have to compile and link file1.c.  Not sure if this makes sense or not.  It just seems that with a large number of files, things can get confusing and disorganized.

Use the -o flag. That stops the compilation process just before the linking process and gives you unlinked object files (.o). Then, when you're ready, you just pass gcc those object files and they'll be linked (gcc automatically looks at the file's extension to know from where to resume compilation).

> **swappo1 said:**
> How do I create a makefile?  Is the makefile called from within the C program?

A Makefile is a script file. Very simply put, "GNU Make" is another programming language... The Makefile are run by the "make" program (which uses the Makefile found on the current directory) and automates you any file-manipulation process you want (not just compiling C sources...) Look at: [http://crasseux.com/books/ctutorial/Writing-a-makefile.html#Writing%20a%20makefile](http://crasseux.com/books/ctutorial/Writing-a-makefile.html#Writing%20a%20makefile)

---

### Post by dwhitney67 on 2008-10-20
> **swappo1 said:**
> Hello,

I want to compile and link two files in C.  I am using Schaum's Programming With C which uses Boreland C in windows.  I am not sure how to apply this to compile and link multiple files within linux.  Here is what I have:

file1.c
[PHP]#include <stdio.h>		// saved as file1.c

extern void output(void);		//function prototype

main()
{
	output();
}
[/PHP]

file2.c
[PHP]extern void output(void)		// external function definition
{								// saved as file2.c
	printf("Hello, there");
	return;
}[/PHP]
...

If you want to learn C programming, I would pick up (or reference) a more up-to-date guide/tutorial than the one you have.  Here's one such guide:  [http://www.cprogramming.com/tutorial.html#ctutorial](http://www.cprogramming.com/tutorial.html#ctutorial)

Nevertheless, here's how Schaum should have presented the exercise:

For file1.c:
[php]
extern void output();

int main()
{
  output();
  return 0;
}
[/php]

For file2.c:
[php]
#include <stdio.h>

void output()
{
  printf("Hello there!\n");
}
[/php]

To compile under Linux:
```
gcc file1.c file2.c -o output
```

To run under Linux:
```
./output
```

---

### Post by swappo1 on 2008-10-21
Thanks for the help.  I understand where I went wrong now.

---

