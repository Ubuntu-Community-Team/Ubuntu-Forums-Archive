---
title: "C - get segmentation fault right at the start of main"
date: 2014-03-03
forum: Programming Talk
---

### Post by squakie on 2014-03-03
For some reason I'm getting a segment fault for reasons I don't understand.

I run via:```
dave@davePC:~/juno-address-book$ ./adconvert test-addrbook.nv juno testoutput  juno-csv
```

I get:```
Segmentation fault (core dumped)
dave@davePC:~/juno-address-book$ 
```

From this code:```
int main ( int argc, char *argv[] )
{

printf("\n\nbefore argc processing.....\n\n");
   if (argc != 5)
     {
        printf("\n\n************************************************\n");
        printf("You didn't specify all 4 arguement:\n");
        printf("    1st = input address book file\n");
        printf("    2nd = input address book format\n");
        printf("        juno = Juno .nv format\n");
        printf("    3nd = output file\n");
        printf("    4th = type of conversion:\n");
        printf("        gmail-csv = output csv file in gmail format\n");
        printf("        tbird-csv = output csv file in thunderbird format\n");
        printf("Can't continue, stopping......");
        printf("\n\n************************************************\n");
        return -1;
     }
printf("/n/nafter argc processing....\n\n");
```

No output from the printf's - and they are newline terminated.  Shouldn't I at least get the first printf - "before argc processing....." , or am I not understanding how something works again?  This DID work until I added an extra arguement (the 2nd).  It worked with all 4 once.  Ever since I've been getting segmentation faults right away.

I'm trying to clean up my code by adding the command line arguement processing and changing everything over to strings (I got errors in compilation before so I was using char arrays and memcpy - then I found out I was supposed to malloc the strings before I used them ;) )

---

### Post by squakie on 2014-03-03
Well, I just ran it with no arguements and the checking of argc worked:```
./abconvert


before argc processing.....



************************************************
You didn't specify all 4 arguement:
    1st = input address book file
    2nd = input address book format
        juno = Juno .nv format
    3nd = output file
    4th = type of conversion:
        gmail-csv = output csv file in gmail format
        tbird-csv = output csv file in thunderbird format
Can't continue, stopping......

************************************************
```

So it must be somewhere in the next bit of processing - this is the part where I tried converting to strings instead of char arrays.

That immediately following code:```
printf("\n\nparsing input format....\n\n");
  my_input_format = malloc(strlen(argv[3]));
  my_input_format = "\0";
printf("\n\ngetting input type...\n\n");
  strcpy(my_input_format, argv[2]); 
  wrk1 = 0;
printf("\n\n");
  while (wrk1 = 0)
     {
        if (0 == strcmp(my_input_format, "juno"))
            break;
        printf("\n\nInput format unknown: %s\n", my_input_format);
        printf("    Must be:\n");
        printf("        juno for input in Juno .nv format\n");
        printf("(\n");
        printf("*    Can't continue.......aborting\n\n");
     }
printf("\n\ninput type: %s\n\n", my_input_format);


  my_output_format = malloc(strlen(argv[3]));
  strcpy(my_output_format, argv[4]); 
  if (0 == strcmp(my_output_format, "gmail-csv"))
  wrk1 = 0;

  while (wrk1 = 0)
     {
        if (0 ==  strcmp(my_output_format, "gmail-csv"))
            break;
        if (0 == strcmp(my_output_format, "tbird-csv"))
            break;
        printf("\n\nOutput format unknown: %s\n", my_output_format);
        printf("    Must be:\n");
        printf("        gmail-csv for gmail csv format\n");
        printf("        tbird-csv for Thunderbird csv format\n");
        printf("\n");
        printf("*    Can't continue.......aborting\n\n");
     }
```

Where the 2 receiving strings are defined as:```
char * my_input_format;
char * my_output_format;
```

I still don't get any of the printf's from that either.

---

### Post by ofnuts on 2014-03-03
Your code works for me. The problem must be elsewhere.

---

### Post by spjackson on 2014-03-03
> **squakie said:**
> 
```

  my_input_format = malloc(strlen(argv[3]));
  my_input_format = "\0";  /* NO NO NO NO NO */
printf("\n\ngetting input type...\n\n");
  strcpy(my_input_format, argv[2]); 




  my_output_format = malloc(strlen(argv[3]));
  strcpy(my_output_format, argv[4]); 

```

The idiom you are looking for is
```

my_input_format = malloc(1 + strlen(argv[3]);
strcpy(my_input_format, argv[3]); 

```
or more succinctly
```

my_input_format = strdup(argv[3]);

```

Well, I'm not sure whether you want 2 or 3 but you certainly want the same in both lines. Also, throwing away the pointer returned from malloc by
```

  my_input_format = "\0";  /* NO NO NO NO NO */

```
is just insane.


> 
```

  while (wrk1 = 0)

```

This ASSIGNMENT will always evaluate to false, so neither of your loops is entered.  You probably mean
```

  while (wrk1 == 0)

```

---

### Post by squakie on 2014-03-03
Thanks!  All be trying that tongiht! ;)

---

### Post by dwhitney67 on 2014-03-03
> **squakie said:**
> Thanks!  All be trying that tongiht! ;)

Why are you copying the input arguments given to the program?  Do you plan to manipulate them somehow, or are your plans (as you have shown thus far) merely to access them for read-purposes?

You could do something similar to the following if you merely need to read the values, although it too is unnecessary:
```

int main(int argc, char* argv[])
{
    ...

    char* my_input_format = argv[3];    // define a pointer that references argv[3].

    ...
}

```

---

### Post by squakie on 2014-03-03
I actually do read the input and output strings in other functions outside of main.  I'm probably being stupid here again, but I thought you had to define globals outside of main().  So, when I define the globals can I do the same "set"?  I thought those values where actually set by the compiler, the others like you show in main() at run-time.  So, if I need those strings to be global, I assume there is just probably something I don't know right now - like can it say globa char* my_input_format = argv[2]; ?

Thanks for the input - I did change the malloc's to 1+ the string length and it works.  I was thinking strlen retun a relative-1 value so that if I malloc'd just the strlen it would be relative 0 so I would get the extra byte.  Something else I apparently don't have right ;)

I'll be trying some more of the suggestions either later tonight or tomorrow.  I want to get all my screwy code converted over to just using strings.  When that part works - which with your help I *think* I know how to do now - then I can go back and set up the command line arguement receptor strings as you show.  It would be a lot cleaner that way!

Thanks again!

---

### Post by dwhitney67 on 2014-03-03
> **squakie said:**
> I actually do read the input and output strings in other functions outside of main.  I'm probably being stupid here again, but I thought you had to define globals outside of main().  So, when I define the globals can I do the same "set"?  I thought those values where actually set by the compiler, the others like you show in main() at run-time.  So, if I need those strings to be global, I assume there is just probably something I don't know right now - like can it say globa char* my_input_format = argv[2]; ?

Yes, that would indeed work.  However, the question that begs to be asked is why are you declaring global variables?  That's a sign of a poor design.  As for the input parameters to the program, they remain there for the life of the program... but the only 'handle' you have to them is (initially) in the main function.  You can of course pass these 'handles' (pointers) to other functions.  For example:
```

#include <stdio.h>

void printProgramName(const char* name)
{
    printf("Your program has the following name: %s\n", name);
}

int main(int argc, char** argv)
{
    printProgramName(argv[0]);
    return 0;
}

```

> 
Thanks for the input - I did change the malloc's to 1+ the string length and it works.  I was thinking strlen retun a relative-1 value so that if I malloc'd just the strlen it would be relative 0 so I would get the extra byte.  Something else I apparently don't have right ;)

strlen() returns the length of the string; thus for a string like "Hello", there appears to be 5 characters... but are there?  Do not forget that an extra character is there... the NULL character that is used to delimit the end of the string.  Hence the reason you would need to allocate an extra byte if your intent is to make an exact copy of another string.

---

### Post by squakie on 2014-03-04
Ah, see I was thinking the strlen was relative one, while a malloc was relative 0, and hence my mistake.

I'm just using globals throuhgout the program for 2 reasons:

(1) I need things to be available to multiple functions, and I was lazy and didn't want to have to pass arguments in the function calls

(2) I was lazy - I wanted easy to follow "field" names, and I wanted to keep them consistent throughout the program so it would be easier for others to know what the heck I did.  I thought it would be easier for others (ok, me ;) ) to know I was working with "input format type" than argv[2] - just easier to read is all.

- and (C) ;)  - my C is not very good at al (as you can tell)l, so I have been having a tough time just trying to code it as is ;)  

Thanks again for the help!

---

### Post by ofnuts on 2014-03-04
> **squakie said:**
> Ah, see I was thinking the strlen was relative one, while a malloc was relative 0, and hence my mistake.


"Relative" is a concept only applicable to indices. Both malloc/strlen handle sizes that are absolute. However, malloc() allocate the required size, and strlen) report the size of "meaningful" characters in a string **not including the final '\0'**, so it reports one byte less than you need to allocate if you want to copy the string. 


> **squakie said:**
> I'm just using globals throuhgout the program for 2 reasons:

(1) I need things to be available to multiple functions, and I was lazy and didn't want to have to pass arguments in the function calls

(2) I was lazy - I wanted easy to follow "field" names, and I wanted to keep them consistent throughout the program so it would be easier for others to know what the heck I did.  I thought it would be easier for others (ok, me ;) ) to know I was working with "input format type" than argv[2] - just easier to read is all.

- and (C) ;)  - my C is not very good at al (as you can tell)l, so I have been having a tough time just trying to code it as is ;)  

Thanks again for the help!

Take a look at the concept of **struct**, it allows you to keep together related values.

---

### Post by squakie on 2014-03-04
Well, I remember struct, but it's been almost 20 years, so I am basically completely green at all of this again.    Right now I'm having a heck of a time just trying to use strings - sounds stupid I suppose, but I'm really starting over here.  I've read a lot of threads on the net for using strings, yet I don't seem to be able to get past the compilation stage yet.  Everytime it compiles, when I run it I get segmentation faults again.  Put some printf's followed by fflush of stdout so I can where it's going, but I can't make heads or tails of it.  If I don't get how to use something as simple as strings then I must be lost.  I'm printing off the entire thing now so I can look at it as it appears somewhere I either added or dropped a "}" as the compiler is bombing out on the last line of code.

If I can't get these strings figured out, would it be okay to post back and see if you can help me with those?  I want to keep working at it for a while first to see if I can get into my head how these things work again.  At one time smart, but now oh so stupid ;)  It's amazing how 20 years can destroy a career's worth of knowledge if you stopped having to apply it (heh, I'm an old guy!). ;)

Thanks again!

---

### Post by dwhitney67 on 2014-03-04
> **squakie said:**
> It's amazing how 20 years can destroy a career's worth of knowledge if you stopped having to apply it (heh, I'm an old guy!). ;)


There's no need for guesswork, or employing bad practices that you may have learned many years ago.  It seems to me that you should re-learn C, without any preconceptions or bad coding practices, by referring to a good book or a tutorial.  Start from page 1, and work your way through the material.  Don't skip a topic because you think you know it.

Here's a link to [Beej's Guide to C Programming]("http://beej.us/guide/bgc/output/html/singlepage/bgc.html").

---

### Post by squakie on 2014-03-04
Thanks everyone.  The problem isn't solved, but everytime I've come to this forum seeking help, and making it clear that I'm starting over green, everyone seems to want to insult me by saying things like "NO! NO! NO!"  or the good old fashiond "rtfm".

In reality, it's not helping, so I'm closing the thread.

---

### Post by dwhitney67 on 2014-03-04
> **squakie said:**
> Thanks everyone.  The problem isn't solved, but everytime I've come to this forum seeking help, and making it clear that I'm starting over green, everyone seems to want to insult me by saying things like "NO! NO! NO!"  or the good old fashiond "rtfm".

In reality, it's not helping, so I'm closing the thread.

You are not starting from green.  You have preconceived knowledge of the C programming language, and based on the information you have provided in your posts, your approach to certain aspects of the language a questionable.  If you are not interested in having someone with experience teach you the language and best practices for accomplishing a goal, then why are you bothering learning C (or for that matter, anything else)... why not just retire, and enjoy the good life?

---

### Post by trent.josephsen on 2014-03-04
OP has a specific problem he's trying to solve, described [here](http://ubuntuforums.org/showthread.php?t=2208405&page=3&p=12943534#post12943534).

@squakie: If you're really starting over, and your goal here is to achieve exporting an address book and not to re-learn C, then may I suggest using a language other than C? You can probably learn enough Perl to solve the problem at hand in less time than it takes you to de-segfault all your C (and I don't mean that in an insulting way; avoiding segfaults in C takes a lot of care). In fact, you might find [someone has solved your problem already](http://search.cpan.org/~interguru/Mail-Addressbook-Convert-1.1/Convert/Juno.pm). At the very least, you won't find it easy to run into memory issues, because Perl is memory managed.

---

### Post by squakie on 2014-03-04
I was under the impression from the previous post that you wanted me to rtfm and figure it out from there.  Can't hardly post back here when that's the case.

---

### Post by spjackson on 2014-03-04
> **squakie said:**
> Thanks everyone.  The problem isn't solved, but everytime I've come to this forum seeking help, and making it clear that I'm starting over green, everyone seems to want to insult me by saying things like "NO! NO! NO!"  or the good old fashiond "rtfm".

In reality, it's not helping, so I'm closing the thread.
I'm sorry I was unable to help you on this occasion. Good luck with solving your problem.

---

### Post by squakie on 2014-03-04
Thank you!  I have it "sort of" working changing one of the arrays to a string, but my parsing routine isn't working right yet.  I'm afraid to post the code as I'm afraid it will just be another one of those "don't know what you're doing", when it fact I know that and that's why I'm asking for help in the first place.  If I knew the answers, there'd be no sense in posting ;)

---

