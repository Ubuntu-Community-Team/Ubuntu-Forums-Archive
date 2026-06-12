---
title: "Pointers with argv[] in C"
date: 2008-07-29
forum: Programming Talk
---

### Post by systemarpi on 2008-07-29
Hi, I am in a trouble with pointers, I cant be able to pass the value of argv[] to a function.

```

#include <stdio.h>

int main(char argc, char *argv[]){
printf("You have run me with: %s %s",argv[1],argv[2]); //This works perfect
readfile(&argv[1]);
}

void readfile(char *file[]){
printf("The filename is: %s",file[1]);//Got (Null) Here
}

```

Thanks in advance, what I am doing is a compressor I just want to specify the file to compress like:
Komp –f filename –l level_of_compression

---

### Post by LaRoza on 2008-07-29
Change readfile() to:

```

void readfile(char *file)

```

And pass like:
```

readfile(argv[1]);

```

*argv[] is an array of pointers. (I write it like **argv, a pointer to a pointer, but it doesn't matter which way you do it). argv[1] will return a pointer to null terminated character array (string).

---

### Post by sq377 on 2008-07-29
First off, look into getopt
[http://www.gnu.org/software/libtool/manual/libc/Using-Getopt.html#Using-Getopt](http://www.gnu.org/software/libtool/manual/libc/Using-Getopt.html#Using-Getopt)
[PHP]
int main(char argc, char *argv[]){
printf("You have run me with: %s %s",argv[1],argv[2]); //This works perfect
readfile(&argv[1]);
}
[/PHP]

This is wrong, the printf line is pointing to things that might not be there.  If you run this program with no arguments, it should crash.  also you are calling argc as a char, that is wrong.

int main(int argc, char *argv[])
is how you should start main.  argc is the number of arguments that there are.  It should always be at least 1 because it counts the program name as the first argument.  So argv[0] should be the name of the program, anything after that should be arguments.  So what you should do is parse the arguments with a for loop, and look through all of the argv arguments (or use getopt to do this).

[PHP]int i = 0;
for( i = 0; i < argc; i++)
{
     printf("argv[%i]: %s\n", i, argv[i]);
}
[/PHP]  This loop will tell you what all the arguments are when you run your program.

Good luck

---

### Post by systemarpi on 2008-07-29
Thanks a lot, now everything is OK, just to simplify things to someone else, the result code is this:

[PHP]
#include <stdio.h>

int main(int argc, char *argv[]){
…
readfile(argv[1]);
…
}

void readfile(char *file){
…
printf("You have run me with: %s",file);
…
}
[/PHP]

There's more to do (validation, fancy stuff, …) but the main problem is solved, will try getopt at home since I am at work now (Windows…) with nothing to do, so I decide to code my own file-compress algorithm in my free-time.

---

### Post by dwhitney67 on 2008-07-29
> **systemarpi said:**
> ...
Komp –f filename –l level_of_compression
I'm glad you were able to sort out the issue concerning how to pass an argv[] value; I also prefer to declare argv as a char **.

Bear in mind that argv[1], based on the command line example you supplied above, will be "-f", not the filename you desire.

I recommend that you define/implement a chunk of code that employs getopt() (as sq377 had suggested) that correctly determines if the filename and the level of compression are supplied.  It seems that the filename is a requisite, however the level of compression is not (and thus you should have a default value for this).

You can read more about getopt() by running:  $ man 3 getopt

Let us know if you have any further questions.

---

