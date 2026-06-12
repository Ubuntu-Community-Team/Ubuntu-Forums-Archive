---
title: "Code written on Linux, compiled on Unix issues."
date: 2009-01-21
forum: Programming Talk
---

### Post by NJDubois on 2009-01-21
Other than 2 bland warnings I get when I compile a really simple program in linux, everything works fine.

But when I send it to my friend who needed a program for a unix machine, he gets an error when he compiles.

/usr/ccs/bin/ld: Unsatisfied symbols:
   getline (first referenced in /var/tmp//cc6NpPvd.o) (code)

here is the code

  printf(" input(%d) : ", tCounter);
  line_input = (char *) malloc (nbytes + 1);
  bytes_read = getline (&line_input, &nbytes, stdin);

I did some research and found out that getline is a GNU standard, I'm guessing its not a Unix standard.  I have zero experience with Unix, and have fired an email to him asking if he knows what compiler he is using.

This part of the code is desigined to simply get a line of text from the console, is there an easier way?  I spent the most time on this part alone.  line_input is what I need the string entered from the keyboard saved to.

Any idea what I can do to kill this error?

[EDIT] It has to be the stdin part?

Thanks in advanced
Nick

---

### Post by Simian Man on 2009-01-21
Gcc is probably the most popular compiler across all Unix systems (except maybe suncc on Solaris platforms), so he is probably using that.

If that is the case he should be able to use the GNU extensions by #defining _GNU_SOURCE in his source code or, equivalently, by passing the -D_GNU_SOURCE option to gcc.  This basically tells the compiler that you want the gnu extensions which may be turned off by default.

If he doesn't use gcc, then you will have to avoid getline or find the source for it and compile it along with your source.

[EDIT] Reading your code, you aren't even relying on the useful features of getline (you create astring on the heap yourself).  You should be able to easily substitute the [fgets]("http://www.opengroup.org/onlinepubs/009695399/functions/fgets.html") function.

---

### Post by NJDubois on 2009-01-21
Awesome.  Thanks for the extremely fast reply!

He is using

HP-UX 11i v1B.11.11

I will look into the fgets function!

Thanks again.

Nick

---

### Post by NJDubois on 2009-01-21
Ok, I killed getline and am using fgets/  EVerything is working fine on his unix system, but on mine it isn;t

my out put is

output(0) : HELLO&#65533;¸
&#65533;                  &#130;&#9252;&#65533;&#65533;&#65533;&#65533;[¸&#65533;8;

but he gets

output(0) : HELLO

like everything is fine.

why??  lol

thanks
Nick

---

### Post by Zugzwang on 2009-01-22
> **NJDubois said:**
> 
why??  lol

thanks
Nick

My guess:

"fgets" will read a certain number of characters. It might be the case that you have to '\0'-terminate the string (char*) you've got yourself by placing it at after the last char (which you can determine from the number of bytes/characters read).

---

### Post by Cracauer on 2009-01-22
Please post complete runnable programs with problems like this.

The difference between gets and getline is that getline will allocate a new memory area for the string if you don't give it one. Since you pass one in, there's no difference.

The adding of the '\0' is automatic in both but might be omitted if nbytes is just one too short. This is why you should post a complete program, we don't know what it.

The problem with binary garbage being printed might also be on the printing end, which you didn't post either.

---

### Post by Krupski on 2009-01-23
> **NJDubois said:**
> Other than 2 bland warnings I get when I compile a really simple program in linux, everything works fine.

But when I send it to my friend who needed a program for a unix machine, he gets an error when he compiles.

/usr/ccs/bin/ld: Unsatisfied symbols:
   getline (first referenced in /var/tmp//cc6NpPvd.o) (code)

here is the code

  printf(" input(%d) : ", tCounter);
  line_input = (char *) malloc (nbytes + 1);
  bytes_read = getline (&line_input, &nbytes, stdin);


Um... can't you just do this:

```

#include <stdio.h>
#include <stdlib.h>

int
main(void) {

    char buffer[BUFSIZ];

    fprintf(stdout, "Please type something: "); // prompt
    fflush(stdout);

    fgets(buffer, BUFSIZ, stdin); // read stdin to buffer

    fprintf(stdout, "You typed: %s\n", buffer); // display it
    fflush(stdout);

    return(0);

}

```


Should compile and run on anything.

-- Roger

---

### Post by PandaGoat on 2009-01-23
Try doing memset(line_input, '\0', nbytes + 1); before you get input and after you allocate memory. It is in string.h.

---

### Post by Cracauer on 2009-01-23
> **PandaGoat said:**
> Try doing memset(line_input, '\0', nbytes + 1); before you get input and after you allocate memory. It is in string.h.

No, both fgets and getstring append a \0.

He's got a different problem and there's nothing we can do to help him since he didn't post that part of the code.

---

