---
title: "Problem with C"
date: 2009-02-11
forum: Programming Talk
---

### Post by xnerdx on 2009-02-11
Hello! I started reading the C for Dummies book (Yes very much a noob book). The reason being I am new to scripting somewhat, anyones here are my problems:

In linux when I use an for or while loop to run a "bugged" loop just for fun to fill the console with infinant repeats; it works! On Windows however, when I try these loops it simply will not execute the loop, it will print the text and exit. On both systems I use the GCC compiler.

Another problem is in my if else scripting. On both Windows and Linux whenever I try to use any type of if else (if to else or if to if else to else) it always reports that "There is no if statement for the else statement", preventing me from compiling. If anyone could help me that would be great, I am half-way done with the begginers book and will be moving on to a more advanced C book :). So maybe if someone knows of any free C ebooks (The C for dummies I have on a ebook for free NOT a torrent for some reason).
Thanks :)

---

### Post by namegame on 2009-02-11
IF you would post your code, it would be much easier for us to help you.

The if-else error, sounds like a syntax issue, but I can't help you without seeing it.

---

### Post by xnerdx on 2009-02-11
Okay, well I still need to find the windows script I had trouble with, but here is my if else and I guess it's working on linux (Opensuse) BUT I enter 1 and it goes straight to the else, I have had it set as != and ==:
```

#include <stdio.h>
#include <stdlib.h>

int main()
{
	int lmo;
	char en[5];
printf("Enter 1 for a loop");
scanf(en);
lmo=atoi(en);
if(lmo==1)
{
	while(lmo!=1)
		printf("Loop\t");
}
else
printf("Oh no loop");
return(0);
}

```

I will try to find that windows script sorry. But, still could anyone help with this script.

---

### Post by stevescripts on 2009-02-11
I'm not gonna waste the time to fix this.

Please, get a different book, or perhaps google for "C Tutorial" ...
(which will provide over 12 million links)

One last thought, what happens if you enter something other than 1?

BTW, that is not a script - it is C code (and very poorly formatted)

Steve

---

### Post by xnerdx on 2009-02-11
Yes I know it's poorly formatted, I was having a feeling something was wrong other than just me. I had the same problem with a C# book I don't know why... Umm I will just keep on experimenting and reading.

---

### Post by weresheep on 2009-02-11
Hello,

I've reformatted your code and got it working. I've added some comments in various places explaining the changes. I find it very useful to have the man pages for the standard C library calls available. They can be obtained by installing the 'manpages-dev' package. Once installed accessing information on e.g. scanf is as simple as

```
 man 3 scanf
```

where the 3 refers to the section of manual where scanf is located.

```

#include <stdlib.h>
#include <stdio.h>

/* Main should be declared as 'int main(void)' or 
'int main(int argc, char **argv)'. */
int main(void) {
  int lmo;
  /* The character array is not required as we'll get scanf to convert the
  input to a number directly. */
  /*char en[5];*/

  printf("Enter 1 for a loop: ");

  /* Try and read the number directly from STDIN with scanf. */
  if (scanf("%d", &lmo) != 1) {
    fprintf(stderr, "Failed to read number\n");
    exit(EXIT_FAILURE);
  }

  /* Didn't event know scanf would compile like that! Using scanf and
  atoi is redundant as scanf can convert a string to a number if you
  pass it the correct format string "%d" where d is for decimal
  integer. */
  /*scanf(en);
  lmo = atoi(en);*/

  
  if (lmo == 1) {
    /* Assume you want an infinite loop here. Use an empty for loop
    as its a standard way of getting an infinite loop. */
    /*while (lmo != 1) {*/
    for (;;) {
      printf("Loop\t");
    }
  }
  /* Although not required for single line statements, it is good
  practice to ALWAYS add the { } in an if, else, while etc. It makes it
  clear what is and isn't part of the code block. */
  else {
    printf("Oh no loop");
  }

  /* End with a newline so we don't mess the next shell prompt :) */
  putchar('\n');

  return 0;
}

```

-weresheep

---

### Post by patryk77 on 2009-02-11
Unrelated, but I hate the way weresheep put in the comments (no offence ;))

The reason is, sometimes you need to comment out a section of code for testing, like so:

```

// The first section to comment out:

/*

do_something();

// Here is a multi-line comment
// which says the next line 
// will do more stuff
do_more_things();

//finish commenting out the section
*/

buggy_function_needs_to_be_run();

// Another section that i want to comment out
/*

do_yet_another_call();
/* Oh nos! A nested comment!
If we have a lot of those, we can't easily comment out a section */

last_commented_out_function();
*/
```

If you use C++ style /* comments */ and you need to comment out a function or part for testing or any other reason, you will have to change all your comments.

Bad habit to have.

That's it for my rant :)

---

### Post by cmay on 2009-02-11
[http://www.crasseux.com/books/](http://www.crasseux.com/books/)
here is a free e-book. 
good luck

---

### Post by Arylon on 2009-02-11
You could always do this instead...

```

// The first section to comment out:
#if 0

do_something();

// Here is a multi-line comment
// which says the next line 
// will do more stuff
do_more_things();

//finish commenting out the section
#endif

buggy_function_needs_to_be_run();

// Another section that i want to comment out
#if 0

do_yet_another_call();
/* Oh nos! A nested comment!
Oh wait, nevermind. There's no nesting here. */

last_commented_out_function();
#endif
```

It used to be a bad habit to use the C++ style // comments in C code because it was non-standard and some compilers couldn't parse them. It also used to be okay to have "void main(void)", but I guess time, and standards have changed.

---

### Post by xnerdx on 2009-02-11
Wow, thanks a lot to everyone overall whom posted help! I didn't know pretty much anything you added except %d, but I only used it in the printf (never heard of fprintf). Anyways, I will be sure to read the ebooks linked because I can tell this other book is far from my needs :). Also, just because I love the // comment I have used that in my scripts haha I much prefer it opposed to /* */ things, they can get confusing ehh. Anyways, thanks everyone! And now I understand why my windows GCC kept warning me about there not being a new line at the end of the function

---

### Post by weresheep on 2009-02-12
> **patryk77 said:**
> Unrelated, but I hate the way weresheep put in the comments (no offence ;))

The reason is, sometimes you need to comment out a section of code for testing, like so:

I tend to compile my C programs with "-Wall -ansi -pendantic" which means C++/C99 style single line comments are not allowed. And as Arylon pointed out it is possible to conditionally remove code from compilation using the preprossor directive 

```

#if 0

#endif

```

VIM even colours the removed code correctly for me :)

xnerdx: reading and writing in C is actually pretty difficult to get right. There are many subtleties that can catch you out. In addition to the man pages I have find the online ([http://c-faq.com/](http://c-faq.com/)) C FAQ to be a great resource.

To really grok C I advise spending a bit of time understanding the Unix model of "everything is a file" (e.g. STDIN, STDOUT, and STDERR) and the nature of buffered I/O.

-weresheep

---

