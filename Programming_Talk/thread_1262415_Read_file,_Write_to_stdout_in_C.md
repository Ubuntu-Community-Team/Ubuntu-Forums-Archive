---
title: "Read file, Write to stdout in C"
date: 2009-09-09
forum: Programming Talk
---

### Post by DrSammyD on 2009-09-09
Hi, I just installed ubuntu in order to program in C and I'm having a problem with this code.

I'm trying to read a file passed using a name passed in as an argument from the terminal, and write that file to the stdout.

Should this code work?

```
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

main(int argc, char **argv)
{
    int n, fd;
    char buf[5];
    int count = 0;
    while(count < 1)
    {
        if(fd = open(argv[count], O_RDONLY)>0)
        {
            count++;
            n= read(fd, buf, 5);
                if (write(1,buf,n) != n)
                    printf("write error");

            if (n < 0)
            printf("read error");
        }
    else
        printf("Unable to open file");
    }

    exit(0);
}
```
Or am I just a moron at programming in C?

---

### Post by PmDematagoda on 2009-09-09
Could you please first put your code into Code tags, indent them properly and address these small problems as well:-
1) main does not have a type specified for it, this is not allowed as the implicit int rule is no longer as of C99, you have to specify a type, preferably int.

2) You are ending the program with an exit(), why not use return for something like that?

3) argv[count] is not a sensible file to open since it is a binary file(the executable of the program which is running it itself since count is 0), so you will get rubbish, give it a more sensible file like the Xorg file at /var/log/Xorg.0.log or similar as a reference.

---

### Post by DrSammyD on 2009-09-09
So how do I get it to write out to the screen? what is the file descriptor for stdout? isn't it 1? 

```
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

int main(int argc, char **argv)
{
    int n, fd;
    char buf[5];
    int count = 1;
    if(fd = open("/var/log/Xorg.0.log", O_RDONLY)>0)
    {
        n= read(fd, buf, 5);
            if (write(1,buf,n) != n)
                printf("write error");

        if (n < 0)
        printf("read error");
    }
    else
        printf("Unable to open file");

    return(0);
}

```

Eitherway, you're saying this should work? because it isn't sending anything to the terminal.

---

### Post by wmcbrine on 2009-09-09
Is there a reason you're using the low-level POSIX calls (open, read, write) instead of the more usual ANSI C buffered I/O (fopen, fread, fwrite)?

---

### Post by PmDematagoda on 2009-09-10
Compiling both your old and new code with the -Wall option specified for GCC gives:-
```
ex.c: In function ‘main’:
**[COLOR="Red"]ex.c:10: warning: suggest parentheses around assignment used as truth value[/COLOR]**
```
which means this line:-
```
    if (fd = open ("/var/log/Xorg.0.log", O_RDONLY) > 0)
```
this problem is fixed with:-
```
    if ( (fd = open("/var/log/Xorg.0.log", O_RDONLY)) > 0 )
```

---

### Post by PmDematagoda on 2009-09-10
Here is a sample program that can get and output the complete contents of the file(mind you, it isn't perfect):-
```
#include <stdio.h>
#include <errno.h>
#include <string.h>
#include <stdlib.h>

int main(int argc, char **argv)
{
  FILE *test_file;
  char buf[4096];
  if ( (test_file = fopen ("/var/log/Xorg.0.log", "r")) != NULL)
    {
      while (!feof (test_file))
	{
	  fgets (buf, sizeof (buf), test_file);
	  puts (buf);
	}
    }
  else
    {
      printf ("Error opening file: %s\n", strerror (errno));
      exit (EXIT_FAILURE);
    }

  return 0;

}
```

---

### Post by fct on 2009-09-10
argv[0] equals the path of the program. For example, for the command "ls filename" it would be "ls", not "filename".

You must use argv[1], but before check that it's been set by making sure argc == 2.

That way you don't need to set the file name in your source code.

---

### Post by fct on 2009-09-10
> **DrSammyD said:**
> So how do I get it to write out to the screen? what is the file descriptor for stdout? isn't it 1? 

```
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

int main(int argc, char **argv)
{
    int n, fd;
    char buf[5];
    int count = 1;
    if(fd = open("/var/log/Xorg.0.log", O_RDONLY)>0)
    {
        n= read(fd, buf, 5);
            if (write(1,buf,n) != n)
                printf("write error");

        if (n < 0)
        printf("read error");
    }
    else
        printf("Unable to open file");

    return(0);
}

```

Eitherway, you're saying this should work? because it isn't sending anything to the terminal.

To print to stdout, it is much easier to just use:

fprintf(stdout, "%.*s", n, buf);

or

printf("%.*s", n, buf);

---

### Post by dwhitney67 on 2009-09-10
> **fct said:**
> To print to stdout, it is much easier to just use:

fprintf(stdout, ".*s", n, buf);

or

printf(".*s", n, buf);

Actually, it is easier to print the data one wants displayed using the correct syntax for the printf() function.  ;)

```

printf("%s", buf);
fprintf(stdout, "%s", buf);

```

Or am I wrong, and has the C library changed on me since I last looked at it?

---

### Post by fct on 2009-09-10
> **dwhitney67 said:**
> Actually, it is easier to print the data one wants displayed using the correct syntax for the printf() function.  ;)

```

printf("%s", buf);
fprintf(stdout, "%s", buf);

```

Or am I wrong, and has the C library changed on me since I last looked at it?

1. It's correct syntax, and it's not new: [http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)
2. In a char array with no null terminators, using printf("%s",...) on it the code might look beyond the array bounds until it finds a '\0' char in memory or is terminated because of a segmentation fault. That's why I specify the string length, which since it can vary with n is not hard-coded in the format string.

P.S.: Just thought that if the file you're reading has bytes set to 0 in the middle of it (not rare in binaries) printf will incorrectly interpret it as a string terminator, so it will not print the rest of the characters in the array. So it would only work if reading text files.

---

### Post by dwhitney67 on 2009-09-10
> **fct said:**
> 1. It's correct syntax, and it's not new: [http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)
2. In a char array with no null terminators, using printf("%s",...) on it the code might look beyond the array bounds until it finds a '\0' char in memory or is terminated because of a segmentation fault. That's why I specify the string length, which since it can vary with n is not hard-coded in the format string.

P.S.: Just thought that if the file you're reading has bytes set to 0 in the middle of it (not rare in binaries) printf will incorrectly interpret it as a string terminator, so it will not print the rest of the characters in the array. So it would only work if reading text files.

I tested the printf() statement in your previous post under cygwin and it did not work as intended.

Under Ubuntu, I get the following warning:
```

gcc -Wall -pedantic -D_GNU_SOURCE -std=gnu99 printf.c 
printf.c: In function &#8216;main&#8217;:
printf.c:8: warning: too many arguments for format

```

Here's the code I tested with:
```

#include <stdio.h>

int main()
{
   const char* buf = "hello world";
   const int   n   = 5;

   printf(".*s", n, buf);
   return 0;
}

```
Now, what in pray-tell am I missing here?

EDIT:  Nevermind... as in your original post, I am missing the percent sign before the ".*s".  The proper format should be:
```

printf("%.*s", n, buf);

```

---

