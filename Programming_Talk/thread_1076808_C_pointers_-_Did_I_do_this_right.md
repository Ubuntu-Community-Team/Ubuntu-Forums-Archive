---
title: "C pointers - Did I do this right?"
date: 2009-02-21
forum: Programming Talk
---

### Post by Krupski on 2009-02-21
Hi all,

[COLOR="Red"]**[Note: this is not homework and I am not a student]**[/COLOR]

I wanted to make a clone of the "basename()" function which returns the appropriate end of a long path string. For example, inside a program "argv[0]" contains the entire path to the program name, something like:

```

argv[0] = "/usr/local/sbin/my_program"

```

And "basename()" of argv[0] would return this:

```

basename(argv[0]) = "my_program"

```

So, below is what I wrote. It works, but I am wondering if I did it correctly. My question lies with the local buffer "tmp[]" and returning the pointer to it.

If the pointer points to a buffer _local to the function_, is it pointing to valid data?

Since the local buffer "goes away" when the function returns, is the pointer returned by the function valid?

I get the idea that I get a pointer to a buffer which can get trashed or overwritten at any time.

Is my concern valid? If so, how should I do it so that the data remains "valid" (i.e. protected from re-use) throughout the running of the program?

Thanks in advance!

-- Roger

Here's the code (function bolded):

```

////////////////////////////////////////////
// test of basename(); clone
// filename: basetest.c
////////////////////////////////////////////

#include <stdio.h>
#include <string.h>

char *bname(char *p1);


// main() is just to test bname()

int main(int argc, char *argv[])
{
	int c, count;

	char arg[6][BUFSIZ];

	count = argc;
	if(count > 5) { count = 5; } // prevent a segfault!

	for(c = 0; c < count; c++) { // get basenames of all args
		strcpy(arg[c], bname(argv[c]));
    }


	for(c = 0; c < count; c++) { // print basenames
		fprintf(stdout, "Base of argv[%d] = '%s'\n", c, arg[c]);
    }

	return 0; // done
}


[B]
// clone of basename();
// typical use: printf("Basename is %s\n", bname(argv[0]));

char *bname(char *p0)
{
    char tmp[BUFSIZ];
	char *p1;
	char *p2;

	strcpy(tmp, p0); // so we don't modify p0

	p2 = strtok(tmp, "/");

	while(p2 != NULL) { // while current pointer != null
		p1 = p2; // copy current to previous
		p2 = strtok(NULL, "/"); // point to next token
	}
	return p1;
}
[/B]

```


When run, this code produces the following output:

```

root@michael:~/c-progs# /root/c-progs/basetest xx/yy/zz/a1 xx/yy/zz/b2 /xx/yy/zz/c3
Base of argv[0] = 'basetest'
Base of argv[1] = 'a1'
Base of argv[2] = 'b2'
Base of argv[3] = 'c3'

```


Thanks!

---

### Post by Can+~ on 2009-02-21
> **Krupski said:**
> Hi all,

[COLOR="Red"]**[Note: this is not homework and I am not a student]**[/COLOR]

I wanted to make a clone of the "basename()" function which returns the appropriate end of a long path string. For example, inside a program "argv[0]" contains the entire path to the program name, something like:

So, below is what I wrote. It works, but I am wondering if I did it correctly. My question lies with the local buffer "tmp[]" and returning the pointer to it.

If the pointer points to a buffer _local to the function_, is it pointing to valid data?

Since the local buffer "goes away" when the function returns, is the pointer returned by the function valid?

Local variables are set as free space once the function ends. It's not reliable. If you need a buffer that can be seen outside the scope of the function, you'll need to allocate the data with malloc/calloc.

The pointer will still point to the place that the data was stored, but, again, it won't be the same data.

---

### Post by WW on 2009-02-21
Instead of strtok, you could use [strrchr](https://www.opengroup.org/onlinepubs/000095399/functions/strrchr.html).

---

### Post by Krupski on 2009-02-21
> **WW said:**
> Instead of strtok, you could use [strrchr](https://www.opengroup.org/onlinepubs/000095399/functions/strrchr.html).

Seems like I always do things the hard way! "strrchr" is exactly what I need. In fact, I'll bet it's a macro that uses "strtok".

Thanks for the info!

-- Roger

---

### Post by Krupski on 2009-02-21
> **Can+~ said:**
> Local variables are set as free space once the function ends. It's not reliable. If you need a buffer that can be seen outside the scope of the function, you'll need to allocate the data with malloc/calloc.


I don't understand what you mean. Could you possibly show me an example?

Thanks.

-- Roger

---

### Post by Can+~ on 2009-02-21
> **Krupski said:**
> I don't understand what you mean. Could you possibly show me an example?

Thanks.

-- Roger

[PHP]#include <stdlib.h>
#include <stdio.h>
#include <string.h>

// Ask for the pointer of the pointer.
void myfunc(char **p)
{
	// Allocate a buffer
	char *buffer = (char*)malloc((sizeof(char)*20));

	// Copy stuff on it
	strcpy(buffer, "Hello world!");

	// Let's see if it worked...
	printf("String inside: %s (%p)\n", buffer, buffer);

	// Now let's set the pointer of the pointer, to point to the buffer (ugh, confusing)
	// graphically: **p -> *p -> buffer
	*p = buffer;
}

int main(int argc, char **argv)
{
	// Create our string
	char *p;

	// Call the function (above)
	myfunc(&p);
	
	// Check if it came out right.
	printf("String outside: %s (%p)\n", p, p);

	// Free the allocated space.
	free(p);
	
	return 0;
}[/PHP]

On the other hand, you could also define a normal buffer on the top function, then call the function handling a pointer to said buffer, it would be a lot more friendly than using malloc and free.

[PHP]void myfunc(char *buffer)
{
	strcpy(buffer, "Hello world!");
}

int main(int argc, char **argv)
{
	char buffer[20];
	
	myfunc(buffer);
	
	printf("String outside: %s\n", buffer);
	
	return 0;
}[/PHP]

---

### Post by Krupski on 2009-02-21
> **Can+~ said:**
> On the other hand, you could also define a normal buffer on the top function, then call the function handling a pointer to said buffer, it would be a lot more friendly than using malloc and free.

Ah I see. That just looks like a complicated way of doing:

char buffer[20];

Now, what has me confused is that you told me (as I expected) "The pointer will still point to the place that the data was stored, but, again, it won't be the same data.".

And, in my test program I called my subfunction 4 times. Each time it allocated a "BUFSIZ" temporary buffer, then returned the pointer to it.

From what I suspected and what you told me, my program SHOULDN'T have worked (or at least the returned strings should have been corrupted). But they weren't.

Any ideas why?

(By the way, that was cool... how did you post a code sample with syntax highlighting??? - That was neat!)

-- Roger

---

### Post by Can+~ on 2009-02-21
> **Krupski said:**
> Ah I see. That just looks like a complicated way of doing:

char buffer[20];

Now, what has me confused is that you told me (as I expected) "The pointer will still point to the place that the data was stored, but, again, it won't be the same data.".

And, in my test program I called my subfunction 4 times. Each time it allocated a "BUFSIZ" temporary buffer, then returned the pointer to it.

From what I suspected and what you told me, my program SHOULDN'T have worked (or at least the returned strings should have been corrupted). But they weren't.

Any ideas why?

(By the way, that was cool... how did you post a code sample with syntax highlighting??? - That was neat!)

-- Roger

When computers "free" space, be it on hard disk or memory, they don't go there and fill it with zeroes. What it really does, it set the space as over-writeable, so even though the place is set as free, the information may still be there.

That's also why you can recover deleted files sometimes, because they are marked as free space but still not overwritten.

---

### Post by mdurham on 2009-02-21
Krupski, why not pass a buffer for bname() to use from the calling function (main() in your example)? that way the buffer will always exist whilst it's needed and you don't need to mess about with malloc()/free().
Cheers, Mike

---

### Post by Krupski on 2009-02-21
> **Can+~ said:**
> When computers "free" space, be it on hard disk or memory, they don't go there and fill it with zeroes. What it really does, it set the space as over-writeable, so even though the place is set as free, the information may still be there.

That's also why you can recover deleted files sometimes, because they are marked as free space but still not overwritten.

Yes I know that! :)

What I meant was this:

First call allocates a buffer, uses it, de-allocates it and returns a pointer to it.

Nothing has used this memory space *yet* so the pointer points to still-usable data.

Next call allocates a buffer (presumably in the same memory location?), uses it, over-writes what was there previously and finally deallocates the buffer and returns a pointer.

The pointer should point to (temporarily) good data from the SECOND call while the first call's pointer now points to garbage.

Now, in my test program, I called the sub function, then immediately copied the data pointed to into another string (allocated outside the sub). At *that* point in time, the pointer pointed to good data since nothing else had a chance to overwrite it yet.

Next call returned a pointer and that was copied to another string, etc...

Are all of these statements correct?

Now another question: How do ordinary C functions return data???

For example, if I do this:

char string[] = "123.45";
float val;

val = atof(string);

(val now equals 123.45000000)

How does atof() return the data to me??

Isn't it returning a pointer to a buffer it used somewhere internally?

If so, obviously the buffer is de-allocated after use... so how does valid data get returned???

Sorry to bug you with all these questions, but the more I learn the more obsessed I get with learning more! :)

Thanks again for your all of your help... way above the "call of duty"! 

-- Roger

---

### Post by Krupski on 2009-02-21
> **mdurham said:**
> Krupski, why not pass a buffer for bname() to use from the calling function (main() in your example)? that way the buffer will always exist whilst it's needed and you don't need to mess about with malloc()/free().
Cheers, Mike

Yes I could do that.

What has my attention at the moment is figuring out / understanding how functions return data to the caller. Since functions allocate temporary storage to do their work, then de-allocate it and finally return their "result" to the caller, I'm confused as to how data which is supposedly residing in de-allocated, "free for all" memory space, is reliably returned to the caller.

Heck, even the question is confusing! :)

-- Roger

---

### Post by Can+~ on 2009-02-21
> **Krupski said:**
> Are all of these statements correct?

If you depend on allocated pieces of data that could be overwritten, you'll be gambling. If a program grows larger, eventually you'll encounter your own fault and it will blow at your face.

Remember what Murphy said: "If something can go wrong, IT WILL!".

> **Krupski said:**
> How does atof() **return** the data to me??

You just answered your own question.

The thing is that C can return integers, floats, pointers, booleans and characters with ease, not so much with strings (arrays). Strings need to be somewhere and a value needs to be returned, which is a pointer to the first character, so you can't return the string "value" but it's position (which, incidentally, is the "value" of the pointer).

In fact, if you go over the whole C standard library, no function returns a string mallocated, they will usually ask for the string itself or a buffer, and edit it in place.

---

### Post by mmix on 2009-02-22
This is basename.c from coreutils-6.12

```
/* basename -- strip directory and suffix from file names
   Copyright (C) 1990-1997, 1999-2008 Free Software Foundation, Inc.

   This program is free software: you can redistribute it and/or modify
   it under the terms of the GNU General Public License as published by
   the Free Software Foundation, either version 3 of the License, or
   (at your option) any later version.

   This program is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
   GNU General Public License for more details.

   You should have received a copy of the GNU General Public License
   along with this program.  If not, see <http://www.gnu.org/licenses/>.  */

/* Usage: basename name [suffix]
   NAME is a file name; SUFFIX is a suffix to strip from it.

   basename /usr/foo/lossage/functions.l
   => functions.l
   basename /usr/foo/lossage/functions.l .l
   => functions
   basename functions.lisp p
   => functions.lis */

#include <config.h>
#include <getopt.h>
#include <stdio.h>
#include <sys/types.h>

#include "system.h"
#include "long-options.h"
#include "error.h"
#include "quote.h"

/* The official name of this program (e.g., no `g' prefix).  */
#define PROGRAM_NAME "basename"

#define AUTHORS proper_name ("FIXME unknown")

/* The name this program was run with. */
char *program_name;

void
usage (int status)
{
  if (status != EXIT_SUCCESS)
    fprintf (stderr, _("Try `%s --help' for more information.\n"),
         program_name);
  else
    {
      printf (_("\
Usage: %s NAME [SUFFIX]\n\
  or:  %s OPTION\n\
"),
          program_name, program_name);
      fputs (_("\
Print NAME with any leading directory components removed.\n\
If specified, also remove a trailing SUFFIX.\n\
\n\
"), stdout);
      fputs (HELP_OPTION_DESCRIPTION, stdout);
      fputs (VERSION_OPTION_DESCRIPTION, stdout);
      printf (_("\
\n\
Examples:\n\
  %s /usr/bin/sort       Output \"sort\".\n\
  %s include/stdio.h .h  Output \"stdio\".\n\
"),
          program_name, program_name);
      emit_bug_reporting_address ();
    }
  exit (status);
}

/* Remove SUFFIX from the end of NAME if it is there, unless NAME
   consists entirely of SUFFIX. */

static void
remove_suffix (char *name, const char *suffix)
{
  char *np;
  const char *sp;

  np = name + strlen (name);
  sp = suffix + strlen (suffix);

  while (np > name && sp > suffix)
    if (*--np != *--sp)
      return;
  if (np > name)
    *np = '\0';
}

int
main (int argc, char **argv)
{
  char *name;

  initialize_main (&argc, &argv);
  program_name = argv[0];
  setlocale (LC_ALL, "");
  bindtextdomain (PACKAGE, LOCALEDIR);
  textdomain (PACKAGE);

  atexit (close_stdout);

  parse_long_options (argc, argv, PROGRAM_NAME, PACKAGE_NAME, VERSION,
              usage, AUTHORS, (char const *) NULL);
  if (getopt_long (argc, argv, "+", NULL, NULL) != -1)
    usage (EXIT_FAILURE);

  if (argc < optind + 1)
    {
      error (0, 0, _("missing operand"));
      usage (EXIT_FAILURE);
    }

  if (optind + 2 < argc)
    {
      error (0, 0, _("extra operand %s"), quote (argv[optind + 2]));
      usage (EXIT_FAILURE);
    }

  name = base_name (argv[optind]);
  strip_trailing_slashes (name);

  /* Per POSIX, `basename // /' must return `//' on platforms with
     distinct //.  On platforms with drive letters, this generalizes
     to making `basename c: :' return `c:'.  This rule is captured by
     skipping suffix stripping if base_name returned an absolute path
     or a drive letter (only possible if name is a file-system
     root).  */
  if (argc == optind + 2 && IS_RELATIVE_FILE_NAME (name)
      && ! FILE_SYSTEM_PREFIX_LEN (name))
    remove_suffix (name, argv[optind + 1]);

  puts (name);
  free (name);

  exit (EXIT_SUCCESS);
}

```

---

### Post by dwhitney67 on 2009-02-22
This is hello.c from my computer:
```

#include <stdio.h>

int main()
{
  printf("hello\n");
  return 0;
}

```

mmix - Was there a point for your post?

---

### Post by the_unforgiven on 2009-02-22
> **dwhitney67 said:**
> This is hello.c from my computer:
```

#include <stdio.h>

int main()
{
  printf("hello\n");
  return 0;
}

```

mmix - Was there a point for your post?
Seconded - neither did I see the actual implementation of the base_name() function :p

@Krupski:
It's far better to just return pointer in the original string instead of allocating buffer in the function and worrying about its lifetime.
After all, the argument passed to bname() is going to be alive in the caller too - so, why not just return a pointer within it? :P
Here is what I mean:
```

#include <stdio.h>
#include <string.h>

char* bname(const char* path) {
	/*
	 * For path => /bin/ls
	 * strrchr() returns /ls
	 * So, we need to advance the pointer by one..
	 */
	char* name = strrchr(path, '/');
	return (name + 1);
}

int main(int argc, char** argv) {
	printf("basename for %s: %s\n", argv[1], bname(argv[1]));
	return 0;
}

```
Note that I haven't done absolutely any error checking in it; especially on argc and argv and most importantly, on the return value of strrchr() - it returns NULL if the second arg is not found in the first - as per the manpage.

My implementation is absolutely not compliant to any of the standards (POSIX or ANSI C), but that's not the point - I'm trying to explain the concept of pointers, arrays and strings ;)

---

### Post by Krupski on 2009-02-22
> **the_unforgiven said:**
> @Krupski:
It's far better to just return pointer in the original string instead of allocating buffer in the function and worrying about its lifetime.
After all, the argument passed to bname() is going to be alive in the caller too - so, why not just return a pointer within it? :P


OK... I *think* I understand what you mean. Please tell me if I did THIS one right (the function in bold) - (Note I used strtok so that I could specify multiple delimiter characters):


```

////////////////////////////////////////////
// test of basename();
// filename: test.c
////////////////////////////////////////////

#include <stdio.h>
#include <string.h>

void bname(char *p0);

int main(int argc, char *argv[])
{
    int c, count;

    char arg[4][BUFSIZ];

    count = argc;

    if(count > 4) { count = 4; } // prevent a segfault!

    for(c = 0; c < count; c++) {
        strcpy(arg[c], argv[c]); // make copies of argv
        bname(arg[c]); // extract basename
    }

    for(c = 0; c < count; c++) { // print basenames
        fprintf(stdout, "Original argv[%d] = '%s'\n", c, argv[c]);
        fprintf(stdout, "Basename: arg[%d] = '%s'\n\n", c, arg[c]);
    }

    return 0; // done
}

[B]
// note this function modifies
// the string passed to it.
void bname(char *p0)
{
    char *p1;

    p1 = strtok(p0, "/");

    while(p1 != NULL) {
        strcpy(p0, p1);
        p1 = strtok(NULL, "/");
    }
}
[/B]

```


BTW, concerning the post by **MMIX**, he may have been answering this post from me:


[quote=Krupski]
Seems like I always do things the hard way! "strrchr" is exactly what I need. In fact, I'll bet it's a macro that uses "strtok".
[/quote]

Anyway, thanks to all who have replied so far... with the help of all you fine people I am learning at a decent rate (well.. decent for me!)  :)

-- Roger

(edit to add another Q): Concerning this line:

```

char arg[4][BUFSIZ];

```

My intent is to create 4 buffers of length "BUFSIZ". Is this right, or should it be

```

char arg[BUFSIZ][4];

```

Or... doesn't it matter?

Thanks.

---

### Post by the_unforgiven on 2009-02-22
> **Krupski said:**
> OK... I *think* I understand what you mean. Please tell me if I did THIS one right (the function in bold) - (Note I used strtok so that I could specify multiple delimiter characters):


```

////////////////////////////////////////////
// test of basename();
// filename: test.c
////////////////////////////////////////////

#include <stdio.h>
#include <string.h>

void bname(char *p0);

int main(int argc, char *argv[])
{
    int c, count;

    char arg[4][BUFSIZ];

    count = argc;

    if(count > 4) { count = 4; } // prevent a segfault!

    for(c = 0; c < count; c++) {
        strcpy(arg[c], argv[c]); // make copies of argv
        bname(arg[c]); // extract basename
    }

    for(c = 0; c < count; c++) { // print basenames
        fprintf(stdout, "Original argv[%d] = '%s'\n", c, argv[c]);
        fprintf(stdout, "Basename: arg[%d] = '%s'\n\n", c, arg[c]);
    }

    return 0; // done
}

[B]
// note this function modifies
// the string passed to it.
void bname(char *p0)
{
    char *p1;

    p1 = strtok(p0, "/");

    while(p1 != NULL) {
        strcpy(p0, p1);
        p1 = strtok(NULL, "/");
    }
}
[/B]

```

Well, it seems to be working, but it doesn't look aesthetically correct.
What I mean by that is there is no need for you to modify the params passed to bname() - instead, you could just return the pointer p1.

There are many threads in this forum which correctly point out that you shouldn't be modifying params passed to function **unless absolutely necessary** - because then, it's amenable to side-effects.

Also, just moving pointer around is much more efficient than doing strcpy().

So, if I am allowed to modify your code, I'd do it this way:
```

////////////////////////////////////////////
// test of basename();
// filename: test.c
////////////////////////////////////////////

#include <stdio.h>
#include <string.h>

**char*** bname(char *p0);

int main(int argc, char *argv[])
{
    int c, count;

    char arg[4][BUFSIZ];
    **char* bnames[4]; // array of pointers to hold pointers to basenames**

    count = argc;

    if(count > 4) { count = 4; } // prevent a segfault!

    for(c = 0; c < count; c++) {
        strcpy(arg[c], argv[c]); // make copies of argv
        **bnames[c] = bname(arg[c]); // extract basename**
    }

    for(c = 0; c < count; c++) { // print basenames
        fprintf(stdout, "Original argv[%d] = '%s'\n", c, argv[c]);
        fprintf(stdout, "Basename: arg[%d] = '%s'\n\n", c, **bnames[c]**);
    }

    return 0; // done
}


// note this function modifies
// the string passed to it.
**char*** bname(char *p0)
{
    [b]//p2 is used to hold the one-step-behind pointer due to the 
    //conditional in while. i.e. p1 == NULL indicates end-of-string..
    //we need to return value *before* that - i.e. the last value of the 
    //tokanized string.[/b]
    char *p1**, *p2;**

    p1 = strtok(p0, "/");

    while(p1 != NULL) {
        [b]//strcpy(p0, p1);
        p2 = p1;[/b]
        p1 = strtok(NULL, "/");
    }
    **return p2;**
}

```
It's essentially a copy+paste of your code with my changes highlighted in bold.

---

### Post by Krupski on 2009-02-22
> **the_unforgiven said:**
> 
So, if I am allowed to modify your code, I'd do it this way:
.......
It's essentially a copy+paste of your code with my changes highlighted in bold.

Take a look at the very first post in this thread. Didn't I do it exactly the way you suggested in the beginning???

I was told that it was wrong by another user, which is why I was trying all of the convoluted different methods!!

-- Roger

(edit): Looked at it again and made a minor change... what about this:

```

char *bname(char *p0)
{
    char *tmp[BUFSIZ];
    char *p1;
    char *p2;

    *tmp = p0; // so we don't modify p0

    p2 = strtok(*tmp, "/");

    while(p2 != NULL) { // while current pointer != null
    p1 = p2; // copy current to previous
    p2 = strtok(NULL, "/"); // point to next token
    }
    return p1;
}

```

Thanks....

-- Roger

---

### Post by the_unforgiven on 2009-02-22
> **Krupski said:**
> 
(edit to add another Q): Concerning this line:

```

char arg[4][BUFSIZ];

```

My intent is to create 4 buffers of length "BUFSIZ". Is this right, or should it be

```

char arg[BUFSIZ][4];

```

Or... doesn't it matter?

Thanks.
It doesn't matter for the compiler - it's going to allocate the entire memory block in contiguous memory.

However, it matters to the human eye...
We humans are more accustomed to the row-major form of matrices/arrays.

So, for us humans:
**char arg[4][BUFSIZE]**
translates into:
BUFSIZE columns each 4 units high..
That is, there are 4 entries/rows/strings each having BUFSIZE amount of storage.

Whereas,
**char arg[BUFSIZE][4]**
translates into:
4 columns each BUFSIZE units high..
That is, there are BUFSIZE entries/rows/strings each having 4 units of storage.

Take your pick - whatever you prefer ;)

---

### Post by the_unforgiven on 2009-02-22
> **Krupski said:**
> Take a look at the very first post in this thread. Didn't I do it exactly the way you suggested in the beginning???

I was told that it was wrong by another user, which is why I was trying all of the convoluted different methods!!

Well, honestly, I didn't look at the code to start with - but, now I did and it's correct way of doing it. I really don't know about others as to why they told you it was wrong :(

> **Krupski said:**
> 
(edit): Looked at it again and made a minor change... what about this:

```

char *bname(char *p0)
{
    char *tmp[BUFSIZ];
    char *p1;
    char *p2;

    *tmp = p0; // so we don't modify p0

    p2 = strtok(*tmp, "/");

    while(p2 != NULL) { // while current pointer != null
    p1 = p2; // copy current to previous
    p2 = strtok(NULL, "/"); // point to next token
    }
    return p1;
}

```

Thanks....

-- Roger

Your definition of tmp is for creating an array of BUFSIZE no. of char pointers - I don't think that's what you mean it to be..
It could simply be a char* :p
Something like:
```
char* tmp = p0;
```
was sufficient. And then, call strtok() with just tmp, instead of *tmp.

The rest of the code looks OK to me.

---

### Post by Krupski on 2009-02-22
> **the_unforgiven said:**
> It doesn't matter for the compiler - it's going to allocate the entire memory block in contiguous memory.

However, it matters to the human eye...
We humans are more accustomed to the row-major form of matrices/arrays.

So, for us humans:
**char arg[4][BUFSIZE]**
translates into:
BUFSIZE columns each 4 units high..
That is, there are 4 entries/rows/strings each having BUFSIZE amount of storage.

Whereas,
**char arg[BUFSIZE][4]**
translates into:
4 columns each BUFSIZE units high..
That is, there are BUFSIZE entries/rows/strings each having 4 units of storage.

Take your pick - whatever you prefer ;)

Well then [4][BUFSIZ] is what I want because my intent is 4 strings, each "BUFSIZ" long.

I figured that in memory it didn't matter (and when I tried it both worked as I suspected). What I really wanted is what you told me... which one is "correct" to a human reader.

Thanks!

-- Roger

---

### Post by Krupski on 2009-02-22
> **the_unforgiven said:**
> Well, honestly, I didn't look at the code to start with - but, now I did and it's correct way of doing it. I really don't know about others as to why they told you it was wrong :(

Your definition of tmp is for creating an array of BUFSIZE no. of char pointers - I don't think that's what you mean it to be..
It could simply be a char* :p
Something like:
```
char* tmp = p0;
```
was sufficient. And then, call strtok() with just tmp, instead of *tmp.

The rest of the code looks OK to me.

Thanks again! I see now that all I'm really doing is moving pointers around. I have to get the notion of strings as "blocks of data to be copied around" out of my head!  :)

Thanks again so much for all your help! [IMG]http://www.gunsnet.net/forums/images/smilies/OLA.gif[/IMG]

-- Roger

---

### Post by Krupski on 2009-02-22
> **the_unforgiven said:**
> Your definition of tmp is for creating an array of BUFSIZE no. of char pointers

I ended up having to do it this way:

```

char *bname(char *p0, char *delim)
{
    char tmp[BUFSIZ];
    char *p1;
    char *p2;

    strcpy(tmp, p0); // copy to avoid modifying input

    p2 = strtok(tmp, delim);

    while(p2 != NULL) { // while current pointer != null
        p1 = p2; // copy current to previous
        p2 = strtok(NULL, delim); // point to next token
    }
    return p1;
}

```

(note I even added the ability to pass a delimiter to the function!)

I had to copy the input string (pointed to by p0) to tmp so that the "strtok" function would not modify the input string.

Without the copy to tmp, this function trashed the input string (which was argv[]!).

Simply making a *tmp pointer was worthless because it was the same thing as using p0 directly... which again caused strtok to trash the input.

I'm getting it.... slowly but surely!

Thanks again!

-- Roger

---

### Post by PandaGoat on 2009-02-22
One way to do it is to dynamically allocate memory and return a pointer to the memory.  A common way to implement this is to also create a method that frees the memory.  I wrote an example to exemplify this.  It may not really be necessary for what you are doing, but you should still consider it.  It is really nice if you are dealing with structs that require special ways of initializing and freeing.  Anyway:

[php]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef char* directory;

/**
 * newDirectory - create a new directory
 * @path: the path the new directory will represent
 *
 * Allocate memory for a new directory and initialize it and return it.
 **/
directory newDirectory( const char* path )
{
  directory d =  malloc( sizeof( char ) * (strlen( path ) + 1) );
  memmove( d, path, strlen( path ) );
  return d;
}

/**
 * getBaseName - get the right-most directory and return it
 * @d: the directory that we wish to get the base name of
 *
 * Find the last occurence of / and return what follows it.  This
 * returns a new directory which should be freed.
 **/
directory getBaseName( const directory d )
{
  return newDirectory( strrchr( d, '/' ) + 1 );
}

/**
 * freeDirectory - a nice reminder for whoever uses this
 * @d: the directory to free
 *
 * This will free the directory and do anything else if needed.
 **/
void freeDirectory( directory d )
{
  /* do some other stuff if needed */
  free( d );
}

/**
 * printDirectory - print the directory
 * @d: the directory to print
 *
 * This should print the directory to stdout.
 **/
void printDirectory( directory d  )
{
  printf("%s", d);
}

int main( int argc, char** argv  )
{
  directory d = newDirectory( "/home/devin" );
  directory base = getBaseName( d );

  printDirectory( d );
  printf( "\n" );
  printDirectory( base );

  freeDirectory( d );
  freeDirectory( base );
}
[/php]

** After thinking about it for a bit, in this example, you could also just return a pointer to the memory pointed to by d so that it points to the start of the base name instead of allocating new memory.  I'm not sure which would be better, probably allocating new memory for the base.

---

### Post by Krupski on 2009-02-22
> **PandaGoat said:**
> One way to do it is to dynamically allocate memory and return a pointer to the memory.

Thanks for the code sample!

I think (correct me if I'm wrong) that I sort of do "dynamically" allocate the memory in that I declare buffers of a size "BUFSIZ", I copy the basename info to each buffer (string) and then use those strings in my program. They get de-allocated when the program exits.

While the program is running, I need the "basenamed" strings in various places, so there's no point in dynamically allocating and deallocating them *within* the program. I need them as long as the program runs.  :)

Thanks again!

-- Roger

---

### Post by mmix on 2009-02-22
> **dwhitney67 said:**
> This is hello.c from my computer:
```

#include <stdio.h>

int main()
{
  printf("hello\n");
  return 0;
}

```

mmix - Was there a point for your post?

point means nothing, just code. :)

and another basename.c from glibc 2.9

```

/* Return the name-within-directory of a file name.
   Copyright (C) 1996,97,98,2002 Free Software Foundation, Inc.
   This file is part of the GNU C Library.

   The GNU C Library is free software; you can redistribute it and/or
   modify it under the terms of the GNU Lesser General Public
   License as published by the Free Software Foundation; either
   version 2.1 of the License, or (at your option) any later version.

   The GNU C Library is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
   Lesser General Public License for more details.

   You should have received a copy of the GNU Lesser General Public
   License along with the GNU C Library; if not, write to the Free
   Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
   02111-1307 USA.  */

#ifdef HAVE_CONFIG_H
# include <config.h>
#endif

#include <string.h>

#ifndef _LIBC
/* We cannot generally use the name `basename' since XPG defines an unusable
   variant of the function but we cannot use it.  */
# define basename gnu_basename
#endif


char *
basename (filename)
     const char *filename;
{
  char *p = strrchr (filename, '/');
  return p ? p + 1 : (char *) filename;
}
#ifdef _LIBC
libc_hidden_def (basename)
#endif

```

---

### Post by apmcd47 on 2009-02-22
Krupski,

What you have to remember is C is a stack-based language. Every time a function is run, its variables are allocated on the stack, and when it is finished, the variables are de-allocated. When you return a scalar, you return its value, so there is no problem. When you return an array, and a character string is the most popular kind of array, you return the address of that array. This is where the problems begin. From here on I'll refer to strings, although it goes for any array.

As you correctly surmised, when a string is allocated within a function it is put on the stack. When the function exits, the string is still there, but it is at risk of being overwritten by another function - any other function. So there are three possible ways of allocating a string: On the stack and cross your fingers; pass your own buffer to be used by the function (I noticed somebody mention this in the thread); allocate memory which the calling function has to free; use static arrays. I did not see any mention of this last possibility.

It is up to the programmer which is used, but you have already decided that the first should be avoided if at all possible. The second is a good idea - not only the buffer, but the length of the buffer should be passed, and if a buffer overrun occurs, it's the fault of the calling programmer, not the functions programmer. The third method means you can allocate only the memory you need but the caller has to be aware that they have to free the memory. In the fourth case, the string is held elsewhere and is used by all instances of the function; that is if you are writing multi-threaded code your function cannot be used. But you can be guaranteed that the string will not be overwritten by anything other than another call to the function.

As to your question how do programmers know what is being returned by library functions, they read the man page. The author of the function should put something like "This function returns a pointer to a static array" and warn the user to copy it before the function is called again. Similarly if the function uses malloc the author should say so and tell the user they need to free the string when finished with it.

I speak from experience: In a program I maintain a text file is created and sometimes it would have garbage in the middle. I finally discovered the fault: One of the function is use returned an automatically created string, ie one on the stack, which was okay for most runs as the string is immediately copied. But the program had timers to check for new files. When the timer ran the string was overwritten by the functions called by the timer. Changing the string to a static fixed the problem. No, I didn't write the original function!

Personally, I think your original code was correct, except that the buffer (tmp) should have been static, and you should use strncpy to copy at most n characters.

Andrew

---

### Post by dwhitney67 on 2009-02-22
Below is some code I was playing with.  I nicked the basename() from the code posted by mmix to compare with my own bname().

Note that in both cases, a wrong result is reported when the path has a trailing slash character (eg. /tmp/foo/) or if the path contains only a single slash (eg. /).

Anyhow, the "basename" command-line utility correctly accounts for these situations, thus it is clear to me that a copy of the input string is being made.

```

#include <stdio.h>
#include <string.h>

const char* bname(const char* path)
{
  const char* p = path + strlen(path) - 1;

  for (; p != path; --p)
  {
    if (*p == '/') break;
  }

  return (*p == '/' ? p+1 : p);
}

char* basename(const char* path)
{
  char* p = strrchr(path, '/');
  return p ? p + 1 : (char*) path;
}


int main(int argc, char** argv)
{
  const char* path = argv[1];

  printf("bname    for %s is = %s\n", path, bname(path));
  printf("basename for %s is = %s\n", path, basename(path));

  return 0;
}

```

---

### Post by Can+~ on 2009-02-22
> **apmcd47 said:**
> Krupski,

....

Andrew

Great post. Summarized everything so far.

Offtopic: And! it wouldn't be complete with the pythonic approach

[PHP]import os, sys

for path in sys.argv:
	print(path.split("/")[-1])[/PHP]
(python 3.0)

or the built-in function for portability:

[PHP]import os, sys

for path in sys.argv:
	print(os.path.basename(path))[/PHP]

---

### Post by Krupski on 2009-02-22
> **Can+~ said:**
> Great post. Summarized everything so far.
Offtopic: And! it wouldn't be complete with the pythonic approach


Thanks to everyone... and to **apmcd47**, **dwhitney67** and "**can-not**" :) (finally clicked what "Can" + "~" means!)

Until recently, I've been doing all of my programming in assembler (for microcontrollers - Motorola).

I am used to knowing what each byte does and where each buffer is and what every subroutine returns.

With C, lots of things are hidden behind the scenes and I'm not always sure exactly what's happening, what's being returned or how or why.

These past few threads we've been through in the last week or so have really taught me a LOT more about the "feel" of what's going on inside C.

Can't get that from any book.

So, I heartily thank you all who've helped me. I really appreciate it!

(And I'll surely be back with more questions!)

Thanks all!!!

-- Roger

---

