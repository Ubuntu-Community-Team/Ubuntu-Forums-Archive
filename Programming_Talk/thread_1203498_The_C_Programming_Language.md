---
title: "The C Programming Language"
date: 2009-07-03
forum: Programming Talk
---

### Post by pmacdonald on 2009-07-03
Hello,

I am currently just getting started in learning my first programming language.  I searched the web and decided to start with the book "The C Programming Language".  The problem is I am already lost.  I have no idea how to set up the Hello World program.  I have a little experience coding in PHP and HTML but nothing like this.  I'm not sure how to compile, what programs I need to do so, etc...

And with the commands they are giving me, I'm guessing that I need a program to type those into?  I would appreciate any help on getting started.  This is my first venture into the software/programming world.  I start college in a few months and will be majoring in computer science.  Any help would be greatly appreciated.

-Peter

---

### Post by CptPicard on 2009-07-03
Umm... the "K&R book" is a concise language reference, not something to really learn programming from if you're a beginner. I mean, what you need is the gcc compiler and a text editor (install the "build-essentials" package, see the sticky threads), but ... I would suggest that if you're such a beginner, perhaps python would be a better fit for your needs. It is a very discoverable language that, actually, goes quite far in teaching you a lot of things. Not to mention that it is useful in the long run.

---

### Post by amauk on 2009-07-03
first off, you need to install a few programs in order to "build" programs yourself

There's a handy package in the repos that bundles all the essential utilities for compiling c / c++ code

in a terminal, type
```
sudo apt-get install build-essential
```
or search Synaptic for "build-essential" and install it

Now, you write C programs in a normal text file (just like you would php scripts)

create a new file in your text editor of choice, and write out a simple C program

save the file, say as "hello.c" in your home folder

open up a terminal, and compile the program using gcc (Gnu C Compiler - part of the build-essential package you installed)

```
gcc -o hello hello.c
```

that tells the gcc compiler to compile "hello.c" and output the compiled program ( -o for output) to a file called "hello"

You can now run the program by typing
```
./hello
```


*edit*
there's loads of C & C++ tutorials around on the net
you may want to have a look through these
Eg. [http://www.cprogramming.com/tutorial/c/lesson1.html](http://www.cprogramming.com/tutorial/c/lesson1.html)

---

### Post by Krupski on 2009-07-03
> **pmacdonald said:**
> Hello,

I am currently just getting started in learning my first programming language.  I searched the web and decided to start with the book "The C Programming Language".

I would heartily recommend the book "**_Practical C Programming_**" by Steve Qualline [([COLOR="Blue"]**LINK**[/COLOR])]("http://oreilly.com/catalog/9781565923065/").

This book is a perfect balance of being simple enough to get a brand new programmer started, yet still contains enough good info to be a useful reference to a more experienced programmer (although it would be a waste of paper to a PROFESSIONAL C programmer).

K&R's book is one you should hold onto as a reference. Don't use it now... you'll just confuse yourself. But later, you will refer to it often.

Good luck!

-- Roger

---

### Post by soltanis on 2009-07-03
Keep the book, but I heartily recommend you start with an easier language (unless you like steep learning curves).

Come back to C later when you have a better idea of what's going on and you'll have a good introduction to the world of system programming.

---

### Post by Krupski on 2009-07-03
> **pmacdonald said:**
> I have no idea how to set up the Hello World program.

To make a "Hello World" program in C (under Linux I assume?) I would do this:

* Install the Linux C compiler:

```

sudo apt-get install build-essential

```

* Create your first piece of source code. I like the "nano" editor a lot more than the popular VI editor. Never could figure out VI.

So, make yourself a directory to play in:

```

mkdir c-programs
chdir c-programs

```

The name can be whatever YOU like.

Next, start writing the code:

```

nano hello.c

```

Type this in:

```

#include <stdio.h>

int main(void)
{
    printf("Hello, world!\n");
    return 0;
}

```

Now, first I'll explain what each line does. Here is the source code again with comments:

```

#include <stdio.h> /* tell the compiler to use standard functions */

int main(void) /* every program needs a "main" */
               /* the "int" means "main" returns an integer */
               /* the "void" means it takes in nothing */

{ /* open brace starts a "block" of code" */

    printf("Hello, world!\n"); /* use the "printf" function */
                               /* tell it WHAT to print */
                               /* the "\n" means "new line" */

    return 0;                  /* "main" is done, return a zero */
                               /* which usually means "no error" */
} /* close brace ends a "block" of code */
/* obviously the things inside this slash star, star slash stuff are comments */

```

Finish up in nano with control-o (output (write) the file and control-x (exit the editor))

Now, you have to COMPILE this source code into a binary program that Linux can RUN:

```

gcc -Wall -o hello hello.c

```

That line means "run the GCC compiler, show -W(arnings)(all), generate an -o(utput) file named "hello" and compile it from the source code file named "hello.c".

Now you should have two files in your directory... "hello.c" and "hello".

The file "hello" is a binary, executable program that you can run.

So just type "hello" to run it. WOOPS it fails! Why? Because Linux doesn't have your new working directory in it's PATH. So, you instead have to type "./hello" (without the quotes)... that is "dot, slash, hello".

This simply means "run, in this current directory where we are, the program named "hello".

If all goes well, it will print on your console screen.

And NOW the real fun begins!

Good luck!

-- Roger

---

### Post by Krupski on 2009-07-03
> **pmacdonald said:**
> Hello,

I am currently just getting started in learning my first programming language.

Check out this "expanded" version of the hello program to see what else can be done:

```

**#include <stdio.h>**

**int main(void)**
**{**
    /* make a 128 byte buffer and fill it */
    /* with the string "John Doe" */
    /* note all 128 bytes are not used */
    **char buffer[128] = "John Doe";**

    /* make an integer variable and set it */
    /* to the decimal value "21" */
    **int age = 21;**

    /* print a message, and substitute "%s" with */
    /* the contents of "buffer" (i.e. replace %s */
    /* with "John Doe") */
    [B]printf("Hello %s, how are you?\n", buffer);
[/B]
    /* print another message, substitute "%d" with */
    /* the value of a variable named "age" */
    [B]printf("I heard you are %d years old\n", age);
[/B]
    /* all done, return (to linux) with a zero */
    /* which means "no error" */
    **return 0;**
**}**

```

When you compile, then run it, the result (should be):

```

Hello John Doe, how are you?
I heard you are 21 years old

```

Now, if you're wondering what those funny looking "%s" and "%d" things do, just take your C book and lookup the "printf" function. You'll run into the part about "printf formatting".

If you think about it, printf needs to know what TYPE of data you are asking it to print.

If I want to print a STRING, I have to tell printf that I want to print a string by using "%s".

If the thing I want to print is a floating point number (like 123.5), I have to tell printf "floating point" by using %f.

You can even do math inside a function, like this:

printf("If you are %d now, in %d years you will be %d\n", 21, 10, 21+10);

You see? The first %d is replaced with "21", the next one is replaced with "10" and the last one is replaced with "21 plus 10" or 31 (the math is done internally and it prints a "31").

Nothing in C is really any more complex than this. All you need to do is know WHAT you want to accomplish and what C FUNCTIONS are needed to do so.

When, inevitably, you run into POINTERS, don't panic... just ask. Pointers are just as simple, once someone explains them to you.

Speaking of "what C functions are needed to do so", let's say one of your programs needed to copy a string to a buffer. You would do something like this:

```

strcpy(buffer, "John Doe");

```

Obviously this means "copy the string "John Doe" into a buffer named "buffer".

But, the header we have been using so far (stdio.h) doesn't know about string functions!!!

That "strcpy" line above would fail with a COMPILER error "error: &#8216;strcpy&#8217; was not declared in this scope". This means the compiler has no clue what "strcpy" is!

We have to tell it by ADDING, at the top of the source code, another line like this:

```

#include <string.h>

```

How do I KNOW this? I don't. I have to look it up in one of my C books.

Another neat way to do it is to install "man" (manual) pages for C right into Linux... like this:

```

sudo apt-get install manpages-dev

```

THEN, you can simply type "man strcpy" and you'll see this:

```

NAME
       strcpy, strncpy - copy a string

SYNOPSIS
       [COLOR="Red"]**#include <string.h>**[/COLOR]

       char *strcpy(char *dest, const char *src);

       char *strncpy(char *dest, const char *src, size_t n);
.....
.....
.....lots left out of this example....
.....

```

Ah HA! see that line in red? THAT'S how I know which header to include in my source code to make "strcpy" work.

The listing also tells me how to USE strcpy... just in case I forgot (or can't find my K&R book).

Lots 'O fun awaits you! Good luck!

-- Roger

---

### Post by nmccrina on 2009-07-03
Um, for c programming you don't necessarily need to "apt-get install build-essential". I was able to compile a test program without installing it, at least. Just follow the rest of Amauk or Krupski's directions for compiling and running.

---

### Post by c0mput3r_n3rD on 2009-07-03
wow pmacdonald you're really lucky you have so many people giving you such great instructions with explanations! if those instructions along with a text book can't teach you c no one can!

 
-And remember while you program, computers are stupid, they only do exactly what you tell them to!!

---

### Post by Krupski on 2009-07-03
> **nmccrina said:**
> Um, for c programming you don't necessarily need to "apt-get install build-essential". I was able to compile a test program without installing it, at least. Just follow the rest of Amauk or Krupski's directions for compiling and running.

Depends on which distro one installs and whether it's Desktop or Server.

The worst that can happen is a message "build-essential is already the newest version."

Better to get a harmless error message than to follow directions for 1/2 hour only to get "-bash: gcc: command not found"... agreed?

-- Roger

---

### Post by Krupski on 2009-07-03
> **c0mput3r_n3rD said:**
> -And remember while you program, computers are stupid, they only do exactly what you tell them to!!

Think of a shampoo bottle. The directions say "lather - rinse - repeat".

A *human* mind knows that this means wash your hair twice.

A *computer* would execute the loop over and over until all the shampoo was gone... there's nothing telling it how many to do or when to stop.

Computers, exasperatingly, do EXACTLY what they are told to do... which sometimes isn't what the programmer really WANTED.

---

### Post by doas777 on 2009-07-03
I suggest you find a book that concentrates more on learning than on referencing. if your an ubergenius (and well you may be) then mabey it;s right for you, but that is usually not the case. 

here are some book reviews:
[http://www.thefreecountry.com/documentation/cppbooks.shtml](http://www.thefreecountry.com/documentation/cppbooks.shtml)

good luck, and have fun

---

### Post by nmccrina on 2009-07-03
> **Krupski said:**
> Depends on which distro one installs and whether it's Desktop or Server.

The worst that can happen is a message "build-essential is already the newest version."

Better to get a harmless error message than to follow directions for 1/2 hour only to get "-bash: gcc: command not found"... agreed?

-- Roger

Touche. I guess I did make the hasty assumption that the OP also was using the Jaunty Desktop.

---

### Post by amauk on 2009-07-03
> **nmccrina said:**
> Touche. I guess I did make the hasty assumption that the OP also was using the Jaunty Desktop.
OP is using Vista, not Ubuntu
(he PM'd me with a question about my post)

I directed him to a vista forum

---

### Post by JoshuaOne on 2009-07-05
Hi, nice to read that you are also start programming, i am also an newbe on programming/compiling, and I buy the book beginning Linux programming 3rd edition
(I am not a newbe in Linux land)

First install GCC and then do the following in terminal (I guess you work with Linux or OSX)

Please come bak when you have installed GCC, then I can tell you what you can do for helloworld ( i must search it for you on another key)

And i am very interested what you have done in HTML, maybe I going to program a website

Thanks,

Greetings JoshuaOne

> **pmacdonald said:**
> Hello,

I am currently just getting started in learning my first programming language.  I searched the web and decided to start with the book "The C Programming Language".  The problem is I am already lost.  I have no idea how to set up the Hello World program.  I have a little experience coding in PHP and HTML but nothing like this.  I'm not sure how to compile, what programs I need to do so, etc...

And with the commands they are giving me, I'm guessing that I need a program to type those into?  I would appreciate any help on getting started.  This is my first venture into the software/programming world.  I start college in a few months and will be majoring in computer science.  Any help would be greatly appreciated.

-Peter

---

### Post by PharmaPhunk on 2009-07-05
C is a great language. I tend to use it more as a hobby, because it takes me a while to finish stuff. I hated it in the begging but once you start developing useful programs it becomes great fun. The best way is to just read example code. I never liked text books, they're just so dull. It's best to go out, download some source code, compile it, play with it, and see what it does and how it works.

---

