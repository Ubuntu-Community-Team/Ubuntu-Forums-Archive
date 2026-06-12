---
title: "linecount file"
date: 2009-04-30
forum: Programming Talk
---

### Post by jon zendatta on 2009-04-30
hello.i just want to count lines in a file,whats wrong here?

[PHP]#include <stdio.h>

main()
   {
   char filename [12];
   FILE *inp_file;
   int c, n = 0;
   inp_file = fopen(filename, "r");
   do {
      printf("Enter File Name\n");
      scanf("%s", filename);
      if (inp_file == NULL)
         printf("File Does Not Exist\n", filename);
      }
   while((c= getchar()) != EOF );
      {
      if(c == '\n')
      n++;
   printf("%d lines\n", n);
   }
   fclose(inp_file);
   return 0;
   }[/PHP]

---

### Post by smudi on 2009-04-30
1. this is not PHP code, but C code...
2. your second if is called only once, as you have one do-while loop with one if, and a single if after
3. getchar doesn't read from a file but from standard input
4. your filename variable is prone to overflow conditions. 
5. you should explicitly declare return type in function signature
6. you could use command line arguments (argc, argv) instead of asking the user to input the file name after the program already executed

---

### Post by dwhitney67 on 2009-04-30
> **smudi said:**
> 1. this is not PHP code, but C code...
...

Wow, you are almost as smart as my 4-year old!

---

### Post by dwhitney67 on 2009-04-30
> **jon zendatta said:**
> hello.i just want to count lines in a file,whats wrong here?

[PHP]#include <stdio.h>

main()
   {
   char filename [12];
   FILE *inp_file;
   int c, n = 0;
   inp_file = fopen(filename, "r");
   do {
      printf("Enter File Name\n");
      scanf("%s", filename);
      if (inp_file == NULL)
         printf("File Does Not Exist\n", filename);
      }
   while((c= getchar()) != EOF );
      {
      if(c == '\n')
      n++;
   printf("%d lines\n", n);
   }
   fclose(inp_file);
   return 0;
   }[/PHP]

Pretty much everything.  I do not have the patience to point out all of the mistakes in your code; it would almost appear that you have not spent more than 5 minutes fumbling through a C programming book, and merely regurgitated the high-lights that you came across.

So you need to examine a file, and provide the line count... try this:

1.  Determine which file needs to be examined.
2.  Attempt to open the file; exit if an error occurs.
3.  Read each line in the file, and for each successful read, increment a counter.
4.  When the end of the file is found, stop reading.
5.  Report the results.

P.S.  Research these library calls:  fopen(), fgets(), feof(), fclose(), and printf().

---

### Post by soltanis on 2009-05-01
C executes statements the same way you read them; top to bottom, in order.
What you are doing is trying to open the file before you have actually read its name, so what the system is actually doing is taking the random data in the uninitialized filename variable, trying to open a file by that name, more likely than not failing, and...you get the rest.

So first of all, you should as the above poster suggested learn what the statements of the language do. As in, there is no reason this:

```

   do {
      printf("Enter File Name\n");
      scanf("%s", filename);
      if (inp_file == NULL)
         printf("File Does Not Exist\n", filename);
      }

```

Should be wrapped in that "do" statement at all, furthermore, you have no condition at the end (the correct syntax is do { } while(condition)),

And then

```

   inp_file = fopen(filename, "r");

```

Should come after you've read the filename from the user,

```

while((c= getchar()) != EOF );
      {
      if(c == '\n')
      n++;
   printf("%d lines\n", n);
   }

```

Again you have not correctly ordered this statement, since you want to print the number of lines you have AFTER the loop is finished,

And while we're on this subject,

```

   char filename [12];

```

12 characters is kind of short for a filename, don't you think?

Finally, get into the habit of using consistent indentation and whitespace so that people can actually read your programs.

---

### Post by ibuclaw on 2009-05-01
> **jon zendatta said:**
> 
#include <stdio.h>
main()
   {
   char filename [12];

I would have gone along with:
```

int main()
{
   char *filename;

```
> 
   FILE *inp_file;
   int c, n = 0;
   inp_file = fopen(filename, "r");
   do {

You put in fopen far too early, also, I would loose the do bracket.
> 
      printf("Enter File Name\n");
      scanf("%s", filename);
      if (inp_file == NULL)
         printf("File Does Not Exist\n", filename);
      }

After printing "File Does Not Exist", your program should terminate.
> 
   while((c= getchar()) != EOF );

I'm not sure what getchar() is, but you are not passing the file descriptor to the function. I would personally use:
```
((c = fgetc(inp_file)) != EOF)
```
> 
      {
      if(c == '\n')

Some files are formatted to use '\r' as newlines...
> 
      n++;
   printf("%d lines\n", n);
   }

I think your intention is to print the number of lines at the end of the program, not within the lexical scope of the while loop.
But I may be wrong...
> 
   fclose(inp_file);
   return 0;
   }


Regards
Iain

---

