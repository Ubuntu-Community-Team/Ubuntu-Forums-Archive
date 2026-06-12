---
title: "C Problem: Counting lines"
date: 2009-05-16
forum: Programming Talk
---

### Post by matmatmat on 2009-05-16
I have a simple C program that should print the number of lines:
```

#include <stdio.h>
int main(int argc, char *argv[])
{
	int lcount;
	char ch;
	if (argc > 1){
		FILE *f = fopen(argv[0], "r");
		while(! feof(f)){
			ch =getc(f);
			if (ch == "\n"){
				lcount++;
			}
		}
		printf("Number of lines is: %d\n", lcount);
	}
	return (0);
}

```
but when run it outputs this:
```

matio@matio-desktop:~/workspace/c/src$ ./count ~/quotes.txt 
Number of lines is: 134513984

```
which is wrong, why?

---

### Post by sujoy on 2009-05-16
first of all, "lcount" isnt initialised so it starts with garbage value.
use ```
int lcount=0;
``` to declare and initialise it at one go

next, argv[0] is the filename of the program itself, that is "./count" in this case, "~/quotes.txt" is argv[1]

yet another thing, always check if 'f', the file descriptor is "Null" or not, that is, whether the file was successfully opened or not.

and ```
return (0);
```
return is not a function, a keyword, hence the parens are optional.

one thing more, 
```
if (ch == "\n"){
``` this ought to be ```
if (ch == '\n'){ 
``` that is single quote instead of double, around '\n', since its just a character and so is ch

---

### Post by matmatmat on 2009-05-16
Thanks for the reply, I now have this:
```

#include <stdio.h>
int main(int argc, char *argv[])
{
	int lcount = 0;
	char ch;
	if (argc > 1){
		FILE *f = fopen(argv[1], "r");
		if (f == NULL){
		 	printf("Couldn't open the file");
			return 0;
		}
		while(! feof(f)){
			ch =getc(f);
			if (ch == "\n"){
				lcount++;
			}
		}
		printf("Number of lines is: %d\n", lcount);
	}
	return 0;
}

```
but if I run it, it says there are no lines, also when I compile it:
```

matio@matio-desktop:~/Documents/c$ gcc -o count count.c
count.c: In function ‘main’:
count.c:33: warning: comparison between pointer and integer

```

---

### Post by sujoy on 2009-05-16
yes, see the last point in the prev answer.

actually in C, chars are single character and are surrounded by '' (single quotes)
strings, which are character arrays, are surrounded by "" (double quotes)

using a string directly in the expression there refers to its starting (base) address, and the character (ch) is just an integer (the ASCII value) hence the error.

for checking against strings in C you use the strcmp() function in string.h, not needed here since ch is a character and so is '\n'. hence

```
if (ch == '\n') { 
``` gets the job done

---

### Post by matmatmat on 2009-05-16
Thanks, I didn't see the last point!

---

### Post by jon zendatta on 2009-05-16
likewise i tried something similar & get seg fault
[PHP]#include <stdio.h>
int main()
{
   char *filename;
   FILE *inp_file;
   int c;
   long n = 0;

   printf("Enter File Name\n");
   scanf("%s", filename);
   inp_file = fopen(filename, "r");
   if (inp_file == NULL)
   printf("File Does Not Exist\n", filename);
   while((c = fgetc(inp_file)) != EOF)
           {
            if(c == '\n')
            n++;
            printf("%ld lines\n", n);
           }  
   fclose(inp_file);
   return 0;
   }   [/PHP]

---

### Post by hanniph on 2009-05-16
> **jon zendatta said:**
> likewise i tried something similar & get seg fault


You got segmentation fault because you are trying to write into memory pointed by uninitialized pointer - filename.
You need either to allocate memory dynamically or to create storage on the stack for your pointer before writing.

---

