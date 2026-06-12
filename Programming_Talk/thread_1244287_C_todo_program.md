---
title: "C todo program"
date: 2009-08-19
forum: Programming Talk
---

### Post by matmatmat on 2009-08-19
I have the following program which works, apart from the '-r':
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[]){
        FILE *f;
        int optchar;
		char line[300];
        while ((optchar = getopt(argc, argv, "r:a:ldc")) != -1){
                switch (optchar){
                        case 'a':
                                f = fopen("/home/matio/todo.txt", "a");
                                fprintf(f, (char *) strdup (optarg));
                                fprintf(f, "\n");
                                break;
                        case 'l':
                                f = fopen("/home/matio/todo.txt", "r");
                                int count = 1; 
								printf("%2i: ", count);                    
                                while (! feof(f)){
                                        char ch = getc(f);
                                        if (ch == EOF){
                                                break;
                                        }
                                        if (ch == '\n'){
																				
                                                printf("%c", ch);
                                                count++;
                                                ch = getc(f);
                                                if (ch != EOF){
                                                        printf("%2i: ", count);
                                                }
                                                else{
                                                        break;
                                               }
                                        }
                                        printf("%c",ch);
                                }
                                break; 
                        case 'c':
                                f = fopen("/home/matio/todo.txt", "w");
                                fprintf(f, "");
								break;
			case 'r':	
				f = fopen("/home/matio/todo.txt", "r");	
				FILE *f2;					
				f2 = fopen("/home/matio/todo2.txt", "a");											
				int n = atoi(optarg) - 1;
				int i = 0;		
				int i2 = 0;					
				while (fscanf(f, "%s\n", line) != EOF) {
					if (i != n){
						fprintf(f2, "%s\n", line);	
					}
					i++;
				}
                                f = fopen("/home/matio/todo.txt", "w");
                                fprintf(f, "");							
				rename("/home/matio/todo2.txt", "/home/matio/todo.txt");							
               }

       }
}

```
example:
```

matio@matio-desktop:~/Documents/c$ ./todo -l #print todo list (nothing there)
matio@matio-desktop:~/Documents/c$ ./todo -a "Post this to ubuntu forums"
matio@matio-desktop:~/Documents/c$ ./todo -a "Post this to ubuntu forums" # oops, I entered it twice
matio@matio-desktop:~/Documents/c$ ./todo -r 1 #remove the first line of todo.txt
matio@matio-desktop:~/Documents/c$ ./todo -l
 1: this
 2: to
 3: ubuntu
 4: forums
 5: Post
 6: this
 7: to
 8: ubuntu
 9: forums
matio@matio-desktop:~/Documents/c$ #?!

```
(I know making two files is probably the worst way of doing this, but I can't think of any other way to do it)

---

### Post by matmatmat on 2009-08-20
[ BUMP ]
Should I use an array of pointers:
```

char *p[100];
//char line[100]
//line holds a line of the file
p[i] = line;

```

[ BUMP ]

---

### Post by Arndt on 2009-08-20
> **matmatmat said:**
> I have the following program which works, apart from the '-r':
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[]){
        FILE *f;
        int optchar;
		char line[300];
        while ((optchar = getopt(argc, argv, "r:a:ldc")) != -1){
                switch (optchar){
                        case 'a':
                                f = fopen("/home/matio/todo.txt", "a");
                                fprintf(f, (char *) strdup (optarg));
                                fprintf(f, "\n");
                                break;
                        case 'l':
                                f = fopen("/home/matio/todo.txt", "r");
                                int count = 1; 
								printf("%2i: ", count);                    
                                while (! feof(f)){
                                        char ch = getc(f);
                                        if (ch == EOF){
                                                break;
                                        }
                                        if (ch == '\n'){
																				
                                                printf("%c", ch);
                                                count++;
                                                ch = getc(f);
                                                if (ch != EOF){
                                                        printf("%2i: ", count);
                                                }
                                                else{
                                                        break;
                                               }
                                        }
                                        printf("%c",ch);
                                }
                                break; 
                        case 'c':
                                f = fopen("/home/matio/todo.txt", "w");
                                fprintf(f, "");
								break;
			case 'r':	
				f = fopen("/home/matio/todo.txt", "r");	
				FILE *f2;					
				f2 = fopen("/home/matio/todo2.txt", "a");											
				int n = atoi(optarg) - 1;
				int i = 0;		
				int i2 = 0;					
				while (fscanf(f, "%s\n", line) != EOF) {
					if (i != n){
						fprintf(f2, "%s\n", line);	
					}
					i++;
				}
                                f = fopen("/home/matio/todo.txt", "w");
                                fprintf(f, "");							
				rename("/home/matio/todo2.txt", "/home/matio/todo.txt");							
               }

       }
}

```
example:
```

matio@matio-desktop:~/Documents/c$ ./todo -l #print todo list (nothing there)
matio@matio-desktop:~/Documents/c$ ./todo -a "Post this to ubuntu forums"
matio@matio-desktop:~/Documents/c$ ./todo -a "Post this to ubuntu forums" # oops, I entered it twice
matio@matio-desktop:~/Documents/c$ ./todo -r 1 #remove the first line of todo.txt
matio@matio-desktop:~/Documents/c$ ./todo -l
 1: this
 2: to
 3: ubuntu
 4: forums
 5: Post
 6: this
 7: to
 8: ubuntu
 9: forums
matio@matio-desktop:~/Documents/c$ #?!

```
(I know making two files is probably the worst way of doing this, but I can't think of any other way to do it)

You seem to always append to todo2, never clearing it. What does the program do that it shouldn't, you're not telling us that.

---

### Post by matmatmat on 2009-08-20
```

 1: this
 2: to
 3: ubuntu
 4: forums
 5: Post
 6: this
 7: to
 8: ubuntu
 9: forums

```
should be
```

1: Post this to ubuntu forums

```

---

### Post by dwhitney67 on 2009-08-20
I believe you require a format statement (ie. something like "%s") in your first fprintf() below.
```

                        case 'a':
                                f = fopen("/home/matio/todo.txt", "a");
                                fprintf(f, (char *) strdup (optarg));
                                fprintf(f, "\n");
                                break;

```
Also, strdup() allocates memory; since you are not freeing it, you have a memory leak.

As matmatmat pointed out, you should consider reading in the contents of your file into some sort of container.  An array could possibly work, but a linked list would be better.

Once the contents are in the container, it should be easy to remove and add new entries.

You could also consider augmenting your app to support the prioritization of the TODO items.

---

### Post by matmatmat on 2009-08-20
Thanks, I don't know why I used strdup (I wrote this quite a while ago)
[Linked list?]("http://www.macs.hw.ac.uk/~rjp/Coursewww/Cwww/linklist.html")

---

### Post by matmatmat on 2009-08-20
> **dwhitney67 said:**
> I believe you require a format statement (ie. something like "%s") in your first fprintf() below.
```

                        case 'a':
                                f = fopen("/home/matio/todo.txt", "a");
                                fprintf(f, (char *) strdup (optarg));
                                fprintf(f, "\n");
                                break;

```

The "todo -a "whatever" works, it's the -r that doesn't.

I now have:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[]){
        FILE *f;
        int optchar;
		char line[300];
        while ((optchar = getopt(argc, argv, "r:a:ldc")) != -1){
                switch (optchar){
                        case 'a':
                                f = fopen("/home/matio/todo.txt", "a");
                                fprintf(f, (char *) strdup (optarg));
                                fprintf(f, "\n");
                                break;
                        case 'l':
                                f = fopen("/home/matio/todo.txt", "r");
                                int count = 1; 
								printf("%2i: ", count);                    
                                while (! feof(f)){
                                        char ch = getc(f);
                                        if (ch == EOF){
                                                break;
                                        }
                                        if (ch == '\n'){
																				
                                                printf("%c", ch);
                                                count++;
                                                ch = getc(f);
                                                if (ch != EOF){
                                                        printf("%2i: ", count);
                                                }
                                                else{
                                                        break;
                                               }
                                        }
                                        printf("%c",ch);
                                }
                                break; 
                        case 'c':
                                f = fopen("/home/matio/todo.txt", "w");
                                fprintf(f, "");
								break;
			case 'r':	
				f = fopen("/home/matio/todo.txt", "r");	
				FILE *f2;					
				f2 = fopen("/home/matio/todo.txt", "w");											
				char *p[100];
				int n = atoi(optarg) - 1;
				int i = 0;		
				int i2 = 0;					
				while (fscanf(f, "%s\n", line) != EOF) {
					if (i != n){
						p[i2] = &line;
						i2++;
					}
					i++;
				}
				i2 = 0;
		       		fprintf(f2, "");
				f2 = fopen("/home/matio/todo.txt", "a");
                                //error here, the increment
				for (i2 = 0; *p != '\0'; p++)
					i2++;
               }  

       }
}

```
when compiled:
```

todo.c: In function ‘main’:
todo.c:13: warning: incompatible implicit declaration of built-in function ‘strdup’
todo.c:13: warning: format not a string literal and no format arguments
todo.c:54: warning: assignment from incompatible pointer type
todo.c:62: error: lvalue required as increment operand

```
:confused:
(I'm guessing it's because it's trying to do something with the string that is being pointed 'at')

---

### Post by MindSz on 2009-08-20
For the incompatible pointer type warning (p[i2] = &line;) it's because you are trying to assign the address of the pointer to line[0] to a value p[i2].

Remember that when you declare an array of characters, the name of the array is also the address of its first element. Instead you can index the array to get the value at a specific location (e.g. line[i])

For the increment problem, I think it'd be better to index the arrays instead of incrementing the pointer

```
for (i2 = 0; p[i2] != '\0'; i2++)
```

I didn't really try to completely understand your code (I'm at work, so I don't have too much time) but these things might cause problems.

Good luck!!

---

### Post by matmatmat on 2009-08-20
Thanks, it compiles now :D 
I didn't notice the warning about the & (I was only trying it to say if it worked)
I now have:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[]){
        FILE *f;
        int optchar;
		char line[300];
        while ((optchar = getopt(argc, argv, "r:a:ldc")) != -1){
                switch (optchar){
                        case 'a':
                                f = fopen("/home/matio/todo.txt", "a");
                                fprintf(f, (char *) strdup (optarg));
                                fprintf(f, "\n");
                                break;
                        case 'l':
                                f = fopen("/home/matio/todo.txt", "r");
                                int count = 1; 
								printf("%2i: ", count);                    
                                while (! feof(f)){
                                        char ch = getc(f);
                                        if (ch == EOF){
                                                break;
                                        }
                                        if (ch == '\n'){
										
                                                printf("%c", ch);
                                                count++;
                                                ch = getc(f);
                                                if (ch != EOF){
                                                        printf("%2i: ", count);
                                                }
                                                else{
                                                        break;
                                               }
                                        }
                                        printf("%c",ch);
                                }
                                break; 
                        case 'c':
                                f = fopen("/home/matio/todo.txt", "w");
                                fprintf(f, "");
								break;
			case 'r':	
				f = fopen("/home/matio/todo.txt", "r");	
				FILE *f2;					
				f2 = fopen("/home/matio/todo.txt", "w");	
				char *p[100];
				int n = atoi(optarg) - 1;
				int i = 0;		
				int i2 = 0;					
				while (fscanf(f, "%s\n", line) != EOF) {
					if (i != n){
						p[i2] = line;
						i2++;
					}
					i++;
				}
				i2 = 0;
		       		fprintf(f2, "");
				f2 = fopen("/home/matio/todo.txt", "a");
				for (i2 = 0; p[i2] != '\0'; i2++)
		       		{	printf(p[i2]);}	
               }  

       }
}

```
running:
```

matio@matio-desktop:~/Documents/c$ vim todo.c
matio@matio-desktop:~/Documents/c$ gcc todo.c -o todo
todo.c: In function &#8216;main&#8217;:
todo.c:13: warning: incompatible implicit declaration of built-in function &#8216;strdup&#8217;
todo.c:13: warning: format not a string literal and no format arguments
todo.c:54: warning: assignment makes pointer from integer without a cast
todo.c:63: warning: format not a string literal and no format arguments
matio@matio-desktop:~/Documents/c$ ./todo -a "1"
matio@matio-desktop:~/Documents/c$ ./todo -l
 1: 1
matio@matio-desktop:~/Documents/c$ ./todo -r 1
GLIBC_2.1GLIBC_2.1&#65533;@Í&#65533;&#65533;&#65533;&#65533;L$&#65533;T$&#65533;@e&#65533;a: Symbol `H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;' has different size in shared object, consider re-linking
<program name unknown><program name unknown>&#65533;@Í&#65533;&#65533;&#65533;&#65533;L$&#65533;T$&#65533;@e&#65533;a: Symbol `H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;' has different size in shared object, consider re-linking
Segmentation fault
matio@matio-desktop:~/Documents/c$

```
Something to do with overwriting line?

---

### Post by johnl on 2009-08-20
Sorry to post and not help with your question :) but I wanted to reiterate something that was said earlier;  this warning:

```

test.c:21: warning: format not a string literal and no format arguments

```
when using lines like
```
 fprintf(f, (char *) strdup (optarg));
```

is important.  Consider this:

```

$ ./test -l
 1: hello world
$ ./test -a "buy 2% milk from store"
$ ./test -l
 1: hello world
 2: buy 2Successilk from store
$ ./test -a "research %d & %s modifiers"
Segmentation fault

```

Either use fputs or fprintf(fp, "%s", ...) so that any special characters inside the user input don't cause unexpected behavior.

(Also you should free the memory allocated with strdup, but I wouldn't care too much about it in this instance since the program only runs for a short period of time and the amount leaked is minor).

---

### Post by dwhitney67 on 2009-08-20
> **johnl said:**
> ...

Either use fputs or fprintf(fp, "%s", ...) so that any special characters inside the user input don't cause unexpected behavior.

(Also you should free the memory allocated with strdup, but I wouldn't care too much about it in this instance since the program only runs for a short period of time and the amount leaked is minor).

Thanks for stating this again.  I thought the OP understood the post I provided earlier, but I guess he chose to ignore it.  Let's see what action he takes on your post.

---

### Post by matmatmat on 2009-08-21
> **dwhitney67 said:**
> Thanks for stating this again.  I thought the OP understood the post I provided earlier, but I guess he chose to ignore it.  Let's see what action he takes on your post.

Or maybe he was trying to sort out the main problem:
IT DOESN'T WORK!

Maybe if it did work I could put it on the todo list

---

### Post by Arndt on 2009-08-21
> **matmatmat said:**
> Or maybe he was trying to sort out the main problem:
IT DOESN'T WORK!

Maybe if it did work I could put it on the todo list

What causes the main problem is a bunch of errors, and you do need to correct all of them. I suggest using a debugger to step through the program, and compare what the program actually does with your mental picture of it.

One problem that wasn't mentioned yet, I think, is that the contents of the p array are undefined until you assign to it (it's whatever happens to be on the stack). This causes problems when you loop through the array, and let a zero pointer indicate the end.

---

### Post by matmatmat on 2009-08-21
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[]){
	char *s = getenv ("HOME");
        FILE *f;
        int optchar;
	char line[300];
	char p[100];
	strcpy(p, s);
	strcat(p,  "/todo.txt");
        while ((optchar = getopt(argc, argv, "r:a:ldc")) != -1){
                switch (optchar){
                        case 'a':
                                f = fopen(p, "a");
                                fprintf(f, (char *) strdup (optarg));
                                fprintf(f, "\n");
                                break;
                        case 'l':
                                f = fopen(p, "r");
                                int count = 1; 
				printf("%2i: ", count);                    
                                while (! feof(f)){
                                        char ch = getc(f);
                                        if (ch == EOF){
                                                break;
                                        }
                                        if (ch == '\n'){
										
                                                printf("%c", ch);
                                                count++;
                                                ch = getc(f);
                                                if (ch != EOF){
                                                        printf("%2i: ", count);
                                                }
                                                else{
                                                        break;
                                               }
                                        }
                                        printf("%c",ch);
                                }
                                break; 
                        case 'c':
                                f = fopen(p, "w");
                                fprintf(f, "");
								break;
			case 'r':	
				f = fopen(p, "r");	
				FILE *f2;					
				f2 = fopen(p, "w");				
				char *p[100];
				int n = atoi(optarg) - 1;
				int i = 0;		
				int i2 = 0;					
				while (fscanf(f, "%s\n", line) != EOF) {
					if (i != n){
						p[i2] = line[0];
						i2++;
					}
					i++;
				}
				i2 = 0;
		       		fprintf(f2, "");
				f2 = fopen(p, "a");
				for (i2 = 0; p[i2] != '\0'; i2++)
		       		{	printf(p[i2]);}	
               }  

       }
}

```
running gdb:
```

matio@matio-desktop:~/Documents/c/t-do$ gdb todo
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(gdb) run -a "h"
Starting program: /home/matio/Documents/c/t-do/todo -a "h"

Program exited with code 0377.
(gdb) run -r 1
Starting program: /home/matio/Documents/c/t-do/todo -r 1

Program received signal SIGSEGV, Segmentation fault.
0xb7e323a7 in strchrnul () from /lib/tls/i686/cmov/libc.so.6
(gdb) quit
The program is running.  Exit anyway? (y or n) y

```
when compiled without the '-g' & run:
```

matio@matio-desktop:~/Documents/c/t-do$ gcc  todo.c -o todo
todo.c: In function &#8216;main&#8217;:
todo.c:11: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
todo.c:12: warning: incompatible implicit declaration of built-in function &#8216;strcat&#8217;
todo.c:17: warning: incompatible implicit declaration of built-in function &#8216;strdup&#8217;
todo.c:17: warning: format not a string literal and no format arguments
todo.c:58: warning: assignment makes pointer from integer without a cast
todo.c:65: warning: passing argument 1 of &#8216;fopen&#8217; from incompatible pointer type
todo.c:67: warning: format not a string literal and no format arguments
matio@matio-desktop:~/Documents/c/t-do$ ./todo -r 1
matio@matio-desktop:~/Documents/c/t-do$

```

> **Arndt said:**
> 
One problem that wasn't mentioned yet, I think, is that the contents of the p array are undefined until you assign to it (it's whatever happens to be on the stack). This causes problems when you loop through the array, and let a zero pointer indicate the end.
what do you mean?

---

### Post by Arndt on 2009-08-21
> **matmatmat said:**
> ```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[]){
	char *s = getenv ("HOME");
        FILE *f;
        int optchar;
	char line[300];
	char p[100];
	strcpy(p, s);
	strcat(p,  "/todo.txt");
        while ((optchar = getopt(argc, argv, "r:a:ldc")) != -1){
                switch (optchar){
                        case 'a':
                                f = fopen(p, "a");
                                fprintf(f, (char *) strdup (optarg));
                                fprintf(f, "\n");
                                break;
                        case 'l':
                                f = fopen(p, "r");
                                int count = 1; 
				printf("%2i: ", count);                    
                                while (! feof(f)){
                                        char ch = getc(f);
                                        if (ch == EOF){
                                                break;
                                        }
                                        if (ch == '\n'){
										
                                                printf("%c", ch);
                                                count++;
                                                ch = getc(f);
                                                if (ch != EOF){
                                                        printf("%2i: ", count);
                                                }
                                                else{
                                                        break;
                                               }
                                        }
                                        printf("%c",ch);
                                }
                                break; 
                        case 'c':
                                f = fopen(p, "w");
                                fprintf(f, "");
								break;
			case 'r':	
				f = fopen(p, "r");	
				FILE *f2;					
				f2 = fopen(p, "w");				
				char *p[100];
				int n = atoi(optarg) - 1;
				int i = 0;		
				int i2 = 0;					
				while (fscanf(f, "%s\n", line) != EOF) {
					if (i != n){
						p[i2] = line[0];
						i2++;
					}
					i++;
				}
				i2 = 0;
		       		fprintf(f2, "");
				f2 = fopen(p, "a");
				for (i2 = 0; p[i2] != '\0'; i2++)
		       		{	printf(p[i2]);}	
               }  

       }
}

```
running gdb:
```

matio@matio-desktop:~/Documents/c/t-do$ gdb todo
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...
(gdb) run -a "h"
Starting program: /home/matio/Documents/c/t-do/todo -a "h"

Program exited with code 0377.
(gdb) run -r 1
Starting program: /home/matio/Documents/c/t-do/todo -r 1

Program received signal SIGSEGV, Segmentation fault.
0xb7e323a7 in strchrnul () from /lib/tls/i686/cmov/libc.so.6
(gdb) quit
The program is running.  Exit anyway? (y or n) y

```
when compiled without the '-g' & run:
```

matio@matio-desktop:~/Documents/c/t-do$ gcc  todo.c -o todo
todo.c: In function ‘main’:
todo.c:11: warning: incompatible implicit declaration of built-in function ‘strcpy’
todo.c:12: warning: incompatible implicit declaration of built-in function ‘strcat’
todo.c:17: warning: incompatible implicit declaration of built-in function ‘strdup’
todo.c:17: warning: format not a string literal and no format arguments
todo.c:58: warning: assignment makes pointer from integer without a cast
todo.c:65: warning: passing argument 1 of ‘fopen’ from incompatible pointer type
todo.c:67: warning: format not a string literal and no format arguments
matio@matio-desktop:~/Documents/c/t-do$ ./todo -r 1
matio@matio-desktop:~/Documents/c/t-do$

```

Why do you show all this? You should not just run the program in the debugger, you should use the debugger to inspect the variables and execution stack.

First of all, fix those warnings. Some of them are innocuous, but some indicate problems that crash the program.

---

### Post by matmatmat on 2009-08-21
Thanks for the help, now it sort of works. It compiles with no warnings and writes to the file:
```

matio@matio-desktop:~/Documents/c/t-do$ ./todo -a "c"
matio@matio-desktop:~/Documents/c/t-do$ ./todo -a "b"
matio@matio-desktop:~/Documents/c/t-do$ ./todo -a "a"
matio@matio-desktop:~/Documents/c/t-do$ ./todo -l
 1: c
 2: b
 3: a
matio@matio-desktop:~/Documents/c/t-do$ ./todo -r 3
matio@matio-desktop:~/Documents/c/t-do$ ./todo -l
 1: a
 2: a

```
```

			case 'r':	
				f = fopen(p, "r");	
				char *t[100];
				int n = atoi(optarg) - 1;
				int i = 0;		
				int i2 = 0;				
				while (fscanf(f, "%s\n", line) != EOF) {
					if (i != n){
						t[i2] = line;
						i2++;
					}
					i++;
				}
				t[i2] = '\0';
				i2 = 0;
		       		fclose(f);
				f = fopen(p, "w");
				fprintf(f, "");
				fclose(f);
				f = fopen(p, "a");
				for (i2 = 0; t[i2] != '\0'; i2++)
		       		{	
					fprintf(f, "%s\n", t[i2]);
				}	

```

---

### Post by dwhitney67 on 2009-08-21
Good, I'm glad you got it working.

Here's a solution I came up with:
```

#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>

typedef struct TodoNode
{
   char             todoItem[60];
   struct TodoNode* next;
} TodoNode;


TodoNode* populate_todo_list(FILE* todoFp);
void      write_items_to_file(TodoNode* list, FILE* todoFp);
TodoNode* add_item_to_todo_list(TodoNode* list, const char* todoItem);
TodoNode* remove_item_from_todo_list(TodoNode* list, const unsigned int itemIndex);
void      destroy_todo_list(TodoNode* list);
void      display_todo_list(TodoNode* list);


// main()
//
int main(int argc, char** argv)
{
   char todoFilePath[1024] = {0};
   const char* HOME = getenv("HOME");

   snprintf(todoFilePath, sizeof(todoFilePath) - 1, "%s/todo.txt", (HOME ? HOME : "./"));

   TodoNode* todoList = 0;
   FILE*     fp = fopen(todoFilePath, "r");

   if (fp)
   {
      todoList = populate_todo_list(fp);
      fclose(fp);
   }


   if (argc == 1)
   {
      // if no cmd-line args, just display the list
      display_todo_list(todoList);
   }
   else
   {
      int optchar     = -1;
      int changesMade = 0;

      while ((optchar = getopt(argc, argv, "r:a:ldc?")) != -1)
      {
         switch (optchar)
         {
         case 'r':   // remove a todo entry
             todoList = remove_item_from_todo_list(todoList, atoi(optarg));
             changesMade = 1;
             break;

         case 'a':   // add todo entry
             todoList = add_item_to_todo_list(todoList, optarg);
             changesMade = 1;
             break; 

         case 'l':   // display todo list
         case 'd':
             display_todo_list(todoList);
             break; 

         case 'c':   // clear todo list
             destroy_todo_list(todoList);
             todoList = 0;
             changesMade = 1;
             break;

         case '?':   // list help
             printf("Usage: %s [-r <item index>] [-a <todo action>] [-l] [-d] [-c]\n", argv[0]);
             break;
         }
      }

      if (changesMade)
      {
         if (todoList == 0)
         {
            unlink(todoFilePath);
         }
         else
         {
            FILE* fp = fopen(todoFilePath, "w");
            write_items_to_file(todoList, fp);
            fclose(fp);
         }
      }
   }

   if (todoList != 0)
   {
      destroy_todo_list(todoList);
   }

   return 0;
}


// populate_todo_list()
//
TodoNode* populate_todo_list(FILE* todoFp)
{
   char todoItem[60] = {0};
   TodoNode* head = 0;
   TodoNode* tail = 0;

   while (fgets(todoItem, sizeof(todoItem), todoFp))
   {
      // strip newline from todoItem string
      todoItem[strlen(todoItem) - 1] = '\0';

      TodoNode* node = malloc(sizeof(TodoNode));
      strncpy(node->todoItem, todoItem, sizeof(node->todoItem) - 1);
      node->next = 0;

      if (head == 0)
      {
         head = node;
         tail = head;
      }
      else
      {
         tail->next = node;
         tail       = node;
      }
   }

   return head;
}


// write_items_to_file()
//
void write_items_to_file(TodoNode* list, FILE* todoFp)
{
   if (list != 0 && todoFp != 0)
   {
      for (TodoNode* node = list; node; node = node->next)
      {
         fprintf(todoFp, "%s\n", node->todoItem);
      }
   }
}


// add_item_to_todo_list()
//
TodoNode* add_item_to_todo_list(TodoNode* list, const char* todoItem)
{
   TodoNode* node = malloc(sizeof(TodoNode));
   strncpy(node->todoItem, todoItem, sizeof(node->todoItem) - 1);
   node->next = 0;

   if (list == 0)
   {
      list = node;
   }
   else
   {
      // find the tail of the list
      TodoNode* tail = list;

      while (tail && tail->next != 0) tail = tail->next;

      tail->next = node;
   }

   return list;
}


// remove_item_from_todo_list()
//
TodoNode* remove_item_from_todo_list(TodoNode* list, const unsigned int itemIndex)
{
   if (list == 0) return 0;

   TodoNode* node = list;

   if (itemIndex == 1)
   {
      // remove the head entry in todo list
      list = node->next;
      free(node);
   }
   else
   {
      unsigned int count = 0;
      TodoNode*    prev  = 0;

      while (node && ++count != itemIndex)
      {
         prev = node;
         node = node->next;
      }

      if (node)
      {
         prev->next = node->next;
         free(node);
      }
   }

   return list;
}


// destroy_todo_list()
//
void destroy_todo_list(TodoNode* list)
{
   TodoNode* node = list;

   while (node != 0)
   {
      TodoNode* destroyNode = node;
      node = node->next;
      free(destroyNode);
   }
}


// display_todo_list()
//
void display_todo_list(TodoNode* list)
{
   unsigned int count = 0;

   printf("\nTODO LIST:\n");
   printf("-----------------------------\n");
   for (TodoNode* node = list; node; node = node->next)
   {
      printf("%d: \t%s\n", ++count, node->todoItem);
   }
   printf("-----------------------------\n\n");
}

```

---

### Post by matmatmat on 2009-08-21
Sort of works, it only writes the last number:
```

$todo -l
1: foo
2: bar
3: 1
4: 2
$todo -r 2 #should remove only bar
$todo -l #it's written the last one 3 times  
1: 2
2: 2
3: 2

```

---

### Post by Arndt on 2009-08-21
> **matmatmat said:**
> Sort of works

Sort of a useless comment.

---

### Post by matmatmat on 2009-08-21
> **matmatmat said:**
> Sort of works, it only writes the last number:


Is that more descriptive

---

### Post by Arndt on 2009-08-21
> **matmatmat said:**
> Is that more descriptive

Certainly. Probably a 'strdup' missing somewhere.

---

### Post by dwhitney67 on 2009-08-21
> **matmatmat said:**
> Is that more descriptive

Well, I for one understand what you were stating earlier.

When I stated that your program "works" I was merely being sarcastic.

It seems you enjoy pounding the HDD and writing slow/inefficient programs.  The code that you wrote for the 'r' option opens the file 3 times!

Why not take a step back, deposit your ego at curbside, and revisit the task you are attempting to accomplish.  It is a fairly trivial task, however because you are limiting the number of tools at your disposal, you are making things very difficult for yourself.

I'm sorry if this post offends you, but I get the impression that you want help, and yet at the same time, you don't.

---

### Post by Arndt on 2009-08-21
> **dwhitney67 said:**
> Well, I for one understand what you were stating earlier.



Before he edited it? "Sort of works" was all he wrote. The edit supplied good information.

---

### Post by dwhitney67 on 2009-08-21
> **Arndt said:**
> Before he edited it? "Sort of works" was all he wrote. The edit supplied good information.

Look at the post before the one I posted w/ code.  The OP finally corrected the compiler warnings, but still had issues with removing a TODO entry from his file.

There's no way I would waste my time attempting to correct the code he had written.

---

### Post by matmatmat on 2009-08-21
> **dwhitney67 said:**
> Well, I for one understand what you were stating earlier.

When I stated that your program "works" I was merely being sarcastic.


:confused: ??? :confused:

> **dwhitney67 said:**
> 
It seems you enjoy pounding the HDD and writing slow/inefficient programs. The code that you wrote for the 'r' option opens the file 3 times!

I've been learning c for a few days! I'm guessing that this means that when I use fopen I can say "rw" instead of just "r" or "w", if this is the case I'm sorry, but I didn't know that, to say I "enjoy" this ...!
I asked the question because I was stuck, I am very great full for all the help given.

---

### Post by Arndt on 2009-08-21
> **dwhitney67 said:**
> Look at the post before the one I posted w/ code.  The OP finally corrected the compiler warnings, but still had issues with removing a TODO entry from his file.

There's no way I would waste my time attempting to correct the code he had written.

Sure, but I'm talking about the post after yours, not the one before yours. (And I'm not criticizing anything you wrote, in case I managed to give that impression.)

---

### Post by matmatmat on 2009-08-21
> **Arndt said:**
> Certainly. Probably a 'strdup' missing somewhere.

Thank you! That was what was wrong

---

### Post by dwhitney67 on 2009-08-21
> **Arndt said:**
> Sure, but I'm talking about the post after yours, not the one before yours. (And I'm not criticizing anything you wrote, in case I managed to give that impression.)
I'm sorry if I gave you the impression my post was directed at you; it wasn't.  I was merely attempting to convey to the OP that he should rethink his design, or at a minimum, at least rethink how to update his file.

---

### Post by anudeep on 2009-08-21
Hi,

I ama novice when it comes to programming and especially working with the libraries.

I am a given a task to include these libraries to execute a program similar to this one.

#include "hdf5.h"


When I try to comlie this with the gcc, it says it cannot find the header file hdf5.h

Can anyone help.

---

### Post by dwhitney67 on 2009-08-21
anudeep, please show some "netiquette", and do not hijack a thread with your coding issue.  Please open a separate thread where your question and any help you may receive can be collected in one place.

P.S.  If you open a separate thread, please edit your post on this thread to remove the contents of the post.

---

### Post by anudeep on 2009-08-21
I am sorry!!!

---

