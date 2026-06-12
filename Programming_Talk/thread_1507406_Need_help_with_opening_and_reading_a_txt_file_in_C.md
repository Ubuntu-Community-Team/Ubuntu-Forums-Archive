---
title: "Need help with opening and reading a txt file in C"
date: 2010-06-11
forum: Programming Talk
---

### Post by technmom on 2010-06-11
I'm learning C and will shortly be going on to C++. I need to open a file and read the line then check for a character. For now I just want to print the line out. I get a segmentation error when running. I'm brand new at C. I have really old old programming experience ( a lot of it but very long ago).

Here is my code (don't laugh I'm learning):


#include <stdio.h>
#include <string.h>


int main()

{
    
    int i;
    int length;
    char line [128];
    char fname [128];
    
// Ask for filename of text file 
    printf("Enter c program filename: ");
    FILE *fr = 0;
    fgets (fname, 80, stdin);

    
     //Open file
    
    fr = fopen(fname, "r");
    printf(" %s ", fname);
    
    while ( fgets(line, sizeof(line), fr) != NULL)
    printf("%s\n", line);

 
    return 0;


}

---

### Post by soltanis on 2010-06-11
You don't check to see if you opened the file successfully after the fopen call:

```

if (!(fr = fopen(fname, "r"))) {
    perror("fopen");
    exit(1);
}

```

Trying to read from a file pointer that is NULL will probably cause a segfault.

---

### Post by technmom on 2010-06-11
Okay so I do get an error no such file or directory. Did I say I'm also new to Linux and the file paths.
I am trying to open the same file that I am compiling or another one in the same directory as the executable.
I suppose I need to enter the entire file path.

This brings me to another question. I have these c programs in my home directory because I don't really know the commands to navigate around and to tell terminal what to look for. I would like to organize them in another directory.

Bye the way exit gave me a compile warning: 
mp1.c:26: warning: incompatible implicit declaration of built-in function ‘exit’

---

### Post by dwhitney67 on 2010-06-11
soltanis is correct in that you should check to see if you successfully opened the file before attempting to read from it.

When passing a file name, you need to pass the full path leading to the file; otherwise fopen() will assume the file is in the current directory.

If you do not already have the man-pages on your system, you need to install them; the reason is so that you do not scratch your head when GCC report something trivial like exit() has not been defined.  The man-pages will provide you with the information necessary to know that the header file stdlib.h needs to be included.
```

sudo apt-get install manpages-dev

man 3 exit    # the 3 is used to indicate which section of the man-pages

```

The man-pages will also provide information on fgets().  It would tell you that it will stop reading the stdin input either when the number of characters specified have been reached OR a newline character is read.  The last part concerning the newline is important.

You have fname declared as an array of 128 characters; from your code, you are only attempting to read 80 characters (odd, but whatever).  If you enter "mp1.c", then your buffer is going to have the following in it:  "mp1.c\n"

The call to fopen() will fail each and everytime because it will never find a file called "mp1.c\n".  You, as the programmer, need to remove the newline from fname.  An easy way to do this is as follows:
```

...

printf("Enter C program filename: ");
fgets(fname, sizeof(fname), stdin);

/* remove the newline if it exists */
char* nl = strchr(fname, '\n');

if (nl != NULL)
{
   *nl = '\0';
}

...

/* open the file */
FILE* fr = fopen(fname, "r");

if (fr != NULL)
{
   /* proceed to read from the file. */
}
else
{
   /* error */
}

```

---

### Post by technmom on 2010-06-11
Thanks I'll try that......I do have man pages just did not think to use it. I just threw the 80 in there don't ask why???

---

### Post by technmom on 2010-06-11
Thanks that worked and I learned a little more C today

---

### Post by trent.josephsen on 2010-06-11
> **technmom said:**
> I'm learning C
Okay.
> and will shortly be going on to C++.
Why?  If you're still wrestling with these basic principles in C (no offense), you don't need to be jumping to another language any time soon.  Unless it's just because you decided C was too hard and wanted to go with something simpler (which is perfectly understandable, but C++ would not be your best option in that case).

C and C++ don't share much besides lineage.  If you want to program in C, learn C; if you want to program in C++, learn C++.  But don't learn half of C and go on to supplement it with half of C++; you'll just end up writing badly designed C programs in C++, or vice versa.  Learn to write in a language *idiomatically* before using it in Real Life.

$0.02 :)

---

### Post by technmom on 2010-06-12
Thanks for you input, but I am learning with some other folks. Our main objective is to learn C++ but the instructor is having us do some C. It is not a class for credit but to learn for using in the near future. So I'm not driving the path but have plenty of holes.

---

### Post by dwhitney67 on 2010-06-12
> **technmom said:**
> Thanks for you input, but I am learning with some other folks. Our main objective is to learn C++ but the instructor is having us do some C. It is not a class for credit but to learn for using in the near future. So I'm not driving the path but have plenty of holes.

Unfortunately, your instructor is worth <snip>.  If his/hers goal is too teach C++, then the STL (o)fsream, along with the STL string, would have veen of beter use.

```

std::string fname
std::cout << "Enter filename: ";
std::getline(fname, std::cin);

std::fstream file(fname.c_str(), std::ios::in);
...

```

---

### Post by technmom on 2010-06-13
Maybe you are right about a better way. He didn't suggest anything so what you see is my stumbling effort to do the task nothing from him. No need for criticism.

---

