---
title: "Opinion / Advice: Coding style in C"
date: 2010-05-16
forum: Programming Talk
---

### Post by Krupski on 2010-05-16
Hi all,

I wrote a little utility that has a lot of "if/else" conditions in it. To avoid an indenting nightmare, I tried a "different" way to use the braces.

Please look at the code below and tell me if what I did is bad (from a coding / standards point of view) and if there's any way I can improve or clean up the code so as not to need so many if/else tests.

The "nasty" I did is highlighted in red, BTW...

Thank you in advance!!

```

///////////////////////////////////////////////////////////////////////////
//
// fixcr.c - Convert text to UNIX format, removes trailing spaces
// Copyright 2010 Roger A. Krupski <krupski@acsu.buffalo.edu>
//
// This program is free software: you can redistribute it and/or modify
// it under the terms of the GNU General Public License as published by
// the Free Software Foundation, either version 3 of the License, or
// (at your option) any later version.
//
// This program is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
// GNU General Public License for more details.
//
// You should have received a copy of the GNU General Public License
// along with this program.  If not, see <http://www.gnu.org/licenses/>.
//
///////////////////////////////////////////////////////////////////////////

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>

int readln(FILE*, char*);
int checkexec(char*);
FILE* openread(char*);
FILE* openwrite(char*);
long int getfilesize(FILE*);
char* allocatebuffer(long int);
long int readfile(FILE*, char*);
long int writefile(FILE*, char*);

int main(int argc, char *argv[])
{
	FILE* fp;
	char* buffer;
	long int n, insize, outsize;

	for(n = 1; n < argc; n++)
	{
		/* make sure file is not executable or a dir */
		if(!checkexec(argv[n])) { fprintf(stderr, "Skipping %s (exec or dir)\n", argv[n]); } else {

		/* open file for read */
		if((fp = openread(argv[n])) == NULL) { fprintf(stderr, "Unable to open %s for read\n", argv[n]); } else {

		/* get file size */
		insize = getfilesize(fp);

		/* try to allocate memory for it */
		if((buffer = allocatebuffer(insize)) == NULL) { fprintf(stderr, "Unable to allocate %ld bytes for buffer\n", insize); } else {

		/* read file into allocated buffer */
		readfile(fp, buffer);

		/* open file for write */
		if((fp = openwrite(argv[n])) == NULL) { fprintf(stderr, "Unable to open %s for write\n", argv[n]); } else {

		/* write out cleaned file */
		outsize = writefile(fp, buffer);

		/* deallocate buffer */
		free(buffer);

		/* report what was done */
		fprintf(stdout, "%ld excess char%s removed from %s\n", (insize-outsize), ((insize-outsize) == 1) ? "" : "s", argv[n]);

		[COLOR="Red"]**}}}}**[/COLOR]
	}
	return 0;
}

/* read one line from fp, strip cr/lf/space junk off the end */
int readln(FILE* fp, char* str)
{
	char buf[BUFSIZ];
	int len, flag;

	buf[0] = 0;
	fgets(buf, BUFSIZ, fp);

	len = strlen(buf);
	flag = 0;

	while (len >= 0) {
		if (buf[len] == 0x0A) { flag = 1; }
		if (buf[len] < 0x21) { buf[len] = 0; len--; }
		else { break; }
	}

	if(flag) { len++; buf[len] = 0x0A; }

	len++; buf[len] = 0;
	strncpy(str, buf, BUFSIZ);
	return strlen(str);
}

int checkexec(char* name)
{
	int result;
	result = access(name, X_OK);
	return result;
}

FILE* openread(char* name)
{
	FILE* fp;
	fp = fopen(name, "rb");
	return fp;
}

FILE* openwrite(char* name)
{
	FILE* fp;
	fp = fopen(name, "wb");
	return fp;
}

long int getfilesize(FILE* fp)
{
	long int size;
	fseek(fp, 0L, SEEK_END);
	size = ftell(fp);
	fseek(fp, 0L, SEEK_SET);
	return size;
}

char* allocatebuffer(long int size)
{
	long int x;
	char* buf = (char*)malloc(size + 1);
	if(buf != NULL)	{ for(x = 0; x < size + 1; x++) { buf[x] = 0; } }
	return buf;
}

long int readfile(FILE* fp, char* destin)
{
	long int len;
	char inbuf[BUFSIZ];

	while(!feof(fp)) { len = readln(fp, inbuf); strncat(destin, inbuf, len); }
	fclose(fp);
	return strlen(destin);
}

long int writefile(FILE* fp, char* source)
{
	fprintf(fp, "%s", source);
	fclose(fp);
	return strlen(source);
}

```

---

### Post by schauerlich on 2010-05-16
Personally, instead of have a cascading if/else, I would do something like this:

```
for (i = 0; i < count; ++i) { 
  if (!thing1worked) {
    puts("oops message 1");
    continue;
  } 
  if (!thing2worked) {
    puts("oops message 2");
    continue;
  }
  ...

  do_something_uselful();
}
```

But perhaps I'm not getting the structure of your code - try spreading the braces and elses out more like my code above, yours isn't a very common style that I'm not used to reading.

---

### Post by trent.josephsen on 2010-05-16
It's probably not the best way to go about it.  I normally handle errors that are fatal to the current iteration of a loop, but not fatal to the program itself, with a break or continue to make the else part unnecessary.  My rule is that most of the "action" that goes on in a loop should be going on in the top level of the loop.  But that's just my opinion, and others, I'm sure, disagree -- some even say that break and continue are as bad as goto, which I certainly don't buy.

An alternative way to do this is to make a function or two that does most of your error checking for you, e.g.

```

for (n = 1; n < argc; n++) {
    char *buffer = try_read(argv[n]);
    if (buffer) {
        try_write(argv[n], buffer);
        free(buffer);
    }
}
```

but in my opinion this does little for you because it saves you at most one indentation level before you have to make the same decision again (try writing the functions if you don't know what I mean).

Your way isn't necessarily wrong, but difficult to read.  I have a few other nits to pick with it, namely using assignment statements in control conditions (which I avoid because it can be confusing and sometimes requires odd placement of parentheses) and commenting practice... I rewrote your main as I would have written it and ran it through indent -kr; this is what I got:

```
int main(int argc, char *argv[])
{
    FILE *fp;
    char *buffer;
    long int n, insize, outsize;


    for (n = 1; n < argc; n++) {
	/* make sure file is not executable or a dir */
	if (!checkexec(argv[n])) {
	    fprintf(stderr, "Skipping %s (exec or dir)\n", argv[n]);
	    continue;
	}

	/* open file for read */
	fp = openread(argv[n]);
	if (fp == NULL) {
	    fprintf(stderr, "Unable to open %s for read\n", argv[n]);
	    continue;
	}

	/* get file size */
	insize = getfilesize(fp);

	/* try to allocate memory for it */
	buffer = allocatebuffer(insize);
	if (buffer == NULL) {
	    fprintf(stderr,
		    "Unable to allocate %ld bytes for buffer\n", insize);
	    continue;
	}

	/* read file into allocated buffer */
	readfile(fp, buffer);

	/* open file for write */
	fp = openwrite(argv[n]);
	if (fp == NULL) {
	    fprintf(stderr, "Unable to open %s for write\n", argv[n]);
	    continue;
	}

	/* write out cleaned file */
	outsize = writefile(fp, buffer);

	/* deallocate buffer */
	free(buffer);

	/* report what was done */
	fprintf(stdout,
		"%ld excess char%s removed from %s\n",
		(insize - outsize),
		((insize - outsize) == 1) ? "" : "s", argv[n]);
    }
    return 0;
}
```

Notice the <80 column max line length.  And speaking of comments, a few of yours seem rather... obvious in nature.  You don't need to tell your reader that a function called "getfilesize" gets the size of a file, or that "free" deallocates memory.  Comments should explain **why** you do something, not **what** you're doing; with properly written code, **what** you're doing should be obvious.  But knowing how to comment just comes with practice, and it's not an exact science.

---

### Post by daimaru on 2010-05-16
take schauerlich's advice and format curly brackets. I prefer it even more extreme than schauerlich. 

for(i=0;i<10;i++)
{
     // do something
}
else
{
     // do something else
}

---

### Post by frostschutz on 2010-05-16
What indenting nightmare are you talking about?

Indenting is a good thing (tm), as it enables you to see the structure of your code at a glance, and if your editor is worth anything, it happens more or less automatically so indenting correctly is something you get for free.

What you are doing there with }}}} in one line on the other hand, that is the real nightmare, because it's impossible to see anymore what's what. A deep if else structure is ugly and in most cases can be avoided by writing the code differently, however in a case where the deep if else structure is necessary or cause too much work to avoid,

then at least indent it properly... please?

---

### Post by Krupski on 2010-05-16
> **schauerlich said:**
> But perhaps I'm not getting the structure of your code - try spreading the braces and elses out more like my code above, yours isn't a very common style that I'm not used to reading.

Well, the code loops through all ARGV[] instances (to do wildcards).

But for each file it *tries* to operate on, the code must:

(1) Be sure the file isn't executable
(2) Open the file
(3) Allocate a buffer for it
(4) Read it in (and fix it)
(5) Write it out
(6) De-allocate the buffer
(7) Report what was done
(8 ) Do the next

After each step, the process has to be aborted and the code go on to the next step if a condition isn't met.

Say I want to operate on "abc.txt" and "xyz.txt" and the first one exists but the second one doesn't, I want the first one operated on the an error message for the second one.

To avoid segfaults, I can't free memory that I didn't allocate, I can't close a file pointer that wasn't opened, etc...

That's why I need to test step by step until I make it to the end of the loop.

Since the code is more or less "segmented" into those individual tests, I thought doing away with the indents and keeping each "segment" on it's own lines would be more easily readable.

For example, I thought that something like this:

```

if (buf[len] < 0x21) { buf[len] = 0; len--; }

```

....was better than...

```

    if (buf[len] < 0x21)
    {
        buf[len] = 0;
        len--;
    }

```

...since it took up less space and the related operations were all "in the same room".

To **schauerlich**: I'm not getting what the "continue" function does... could you explain?

What I need is basically:

if (first_ok)
{
    do_second();
}
else
{
    show_error();
}

if (second_ok)
{
   try_third();
}
else
{
    show_error();
}


Those darn braces pile up really quick!

-- Roger

---

### Post by Krupski on 2010-05-16
> **frostschutz said:**
> What indenting nightmare are you talking about?

Indenting is a good thing (tm), as it enables you to see the structure of your code at a glance, and if your editor is worth anything, it happens more or less automatically so indenting correctly is something you get for free.

What you are doing there with }}}} in one line on the other hand, that is the real nightmare, because it's impossible to see anymore what's what. A deep if else structure is ugly and in most cases can be avoided by writing the code differently, however in a case where the deep if else structure is necessary or cause too much work to avoid,

then at least indent it properly... please?

Well, I recall someone (Linus T. maybe?) saying something like "If you have more than X levels of indent you're doing something wrong".

Or am I just nuts? :)

(edit to add): Found it.... "If you need more than 3 levels of indentation, you're screwed anyway, and should fix your program."

That's why I was concerned!

---

### Post by lisati on 2010-05-16
> **Krupski said:**
> Well, I recall someone (Linus T. maybe?) saying something like "If you have more than X levels of indent you're doing something wrong".

Or am I just nuts? :)

(edit to add): Found it.... "If you need more than 3 levels of indentation, you're screwed anyway, and should fix your program."

That's why I was concerned!

I think the idea is to help with clarity of the code: if the screen gets too cluttered, it's harder to follow what the program's doing.

If I understand the opening comments, it looks like part of what you want to do is similar to [this]("http://lisati.myftp.org/page16.html").

BTW: Nice idea to check if it's an executable program!

---

### Post by trent.josephsen on 2010-05-16
The **continue** keyword (it's not a function) jumps to just before the closing } of the inmost enclosing loop block.

```
for (i = 0; i < 10; i++) {
    if (i%2 == 0) {
        continue;
    }
    printf("%d\n", i);
    /* **continue jumps here** */
}
```

That code will skip the remainder of the block (the printf statement) whenever i is evenly divisible by 2.  The increment is still performed and the condition is still tested before the loop body is executed. This code will print out only odd numbers (between 0 and 9 inclusive).

Make sense?

---

### Post by splicerr on 2010-05-16
> **Krupski said:**
> 
What I need is basically:

if (first_ok)
{
    do_second();
}
else
{
    show_error();
}

if (second_ok)
{
   try_third();
}
else
{
    show_error();
}


Those darn braces pile up really quick!

-- Roger

You can also do something like this:

[PHP]
if (do_first() != ok)
    show_error();
else if (do_second() != ok)
    show_error();
else if (do_third() != ok)
    show_error();
[/PHP]But there's no real clean solution here. I'm afraid you'll just have to live with the limitations of the language.

---

### Post by Krupski on 2010-05-16
> **trent.josephsen said:**
> The **continue** keyword (it's not a function) jumps to just before the closing } of the inmost enclosing loop block.

```
for (i = 0; i < 10; i++) {
    if (i%2 == 0) {
        continue;
    }
    printf("%d\n", i);
    /* **continue jumps here** */
}
```

That code will skip the remainder of the block (the printf statement) whenever i is evenly divisible by 2.  The increment is still performed and the condition is still tested before the loop body is executed. This code will print out only odd numbers (between 0 and 9 inclusive).

Make sense?

Well, it didn't make sense until I ran it! Now I get it! Thanks!

BTW, this is what I did:

```

#include <stdio.h>

int main(void)
{
	int i;
	for (i = 0; i < 10; i++) {
		if (i % 2 == 0) {
			printf("before continue %d\n", i);
			continue;
		}
		printf("after continue %d\n", i);
		/* continue jumps here */
	}
}

```

...and the output is...

```

root@michael:~/c-progs# ./test 
before continue 0
after continue 1
before continue 2
after continue 3
before continue 4
after continue 5
before continue 6
after continue 7
before continue 8
after continue 9

```

Thanks for the sample code! Now I get it! [IMG]http://three-dog.homelinux.com/phpBB3/images/smilies/thumbspbig.gif[/IMG]

-- Roger

---

### Post by dwhitney67 on 2010-05-16
> **Krupski said:**
> 
For example, I thought that something like this:

```

if (buf[len] < 0x21) { buf[len] = 0; len--; }

```

....was better than...

```

    if (buf[len] < 0x21)
    {
        buf[len] = 0;
        len--;
    }

```

You are entitled to an opinion... and thus let me give it to you.  You style is crap.  The second style of code you posted is clearer to read, and is often used in the s/w industry.  The K&R format, which was presented earlier is also often used.  However, personally I prefer placing the braces such that they are indented equally, thus forming a clear block of code.

If you are having trouble modularizing your code, or even breaking it into smaller functional components, then say so.  Based on your requirements, the following should get you on your way to completing your **homework assignment**.

```

#include <sys/stat.h>
#include <stdlib.h>
#include <stdio.h>

int isExecutable(const int mode)
{
   return mode & (S_IXUSR | S_IXGRP | S_IXOTH);
}


int main(int argc, char** argv)
{
   --argc; ++argv;

   while (argc-- != 0)
   {
      const char* file = *argv++;
      struct stat buf;

      if (stat(file, &buf) == 0)
      {
         if (isExecutable(buf.st_mode))
         {
            fprintf(stderr, "File %s is executable; ignoring\n", file);
            continue;
         }

         char* buffer = malloc(buf.st_size);

         if (buffer)
         {
            fprintf(stdout, "Processing file %s\n", file);

            // ...
 
            free(buffer);
         }
         else
         {
            fprintf(stderr, "File %s is too big to process.\n", file);
         }
      }
      else
      {
         fprintf(stderr, "File not found: %s\n", file);
      }
   }

   return 0;
}

```

---

### Post by Krupski on 2010-05-16
> **lisati said:**
> I think the idea is to help with clarity of the code: if the screen gets too cluttered, it's harder to follow what the program's doing.

If I understand the opening comments, it looks like part of what you want to do is similar to [this]("http://lisati.myftp.org/page16.html").

BTW: Nice idea to check if it's an executable program!

Thanks for the input. I thought I was making the code LESS cluttered by doing what I did (mostly out of fear of the "too many indents" thing).

I see though that the indents are really OK.

BTW, thanks for pointing me to your sample code. Yes, yours does basically what mine does. Mine also strips out trailing spaces in files (because they annoy me when I browse through code and see all those horrible green "trailing spaces" lines in NANO).

I have a lot of PHP code from a message board that's just littered with trailing spaces and some of them are also CR/LF (Windows) mode... drives me nuts!

As far as checking if a file is set as executable... well you can guess why I do that... I made the almost fatal mistake of "fixing" **_all_** the files in a directory. Thankfully I had the stuff I wrecked backed up! :)

Thanks again for your input and the sample code!

-- Roger

---

### Post by Krupski on 2010-05-16
> **dwhitney67 said:**
> Based on your requirements, the following should get you on your way to completing your **homework assignment**.


It's not homework. I'm 53 years old. I've been out of college for over 30 years.

My employer is a state university, and my work email address is a "buffalo.edu" domain, but I am not a student and none of my stuff is homework (mine or anyone elses).

I know the policy here against doing homework for people and I would not violate that by doing it or by asking for it.

With that said... thanks for the code snippet. I'll play with it, learn how it works and probably incorporate it into my little lousy utility.

(edit to add): Check it out for yourself if you wish: [[COLOR="Blue"]**_LINK_**[/COLOR]]("http://www.buffalo.edu/directory/find-people-detail-page.html?uid=krupski&query=krupski")

-- Roger

---

### Post by dwhitney67 on 2010-05-17
> **Krupski said:**
> 
(edit to add): Check it out for yourself if you wish: [[COLOR="Blue"]**_LINK_**[/COLOR]]("http://www.buffalo.edu/directory/find-people-detail-page.html?uid=krupski&query=krupski")

-- Roger

My apologies.

Normally when I see trivial requirements posted, and which at the same time sort of provides a hint or two at the solution, it appears as a homework assignment.


P.S.  If I were you, I would exercise more caution of posting PII (Personal Identifiable Information) on the web.  In your spare time, read more about PII here: [http://en.wikipedia.org/wiki/Personally_identifiable_information](http://en.wikipedia.org/wiki/Personally_identifiable_information)

---

### Post by Krupski on 2010-05-17
> **dwhitney67 said:**
> My apologies.

Normally when I see trivial requirements posted, and which at the same time sort of provides a hint or two at the solution, it appears as a homework assignment.

Apology not necessary... I've seen a lot of people here try to get their homework done... and then here I come with a ".edu" email address... I probably would have thought the same thing.

As far as "trivial" requirements for a program, what's trivial to one person is beyond the understanding of another.

When I went to school we barely had calculators... (we were just moving away from slide rules!) and there were no "personal computers", nor was anything taught other than Fortran with IBM cards!

I am 100% self taught when it comes to computers and programming. I stick my nose into HTML, PHP, Javascript, C, Basic, Assembler, etc... Jack of all trades, master of none.

So, yeah I'll probably be asking more "trivial" questions in the future. Remember that one doesn't KNOW it until they LEARN it... and I'm still trying to LEARN it... and I will appreciate your posts, comments and examples.

-- Roger

---

### Post by lisati on 2010-05-17
> **Krupski said:**
> 
When I went to school we barely had calculators... (we were just moving away from slide rules!) and there were no "personal computers", nor was anything taught other than Fortran with IBM cards!


:) I remember horrible versions of those cards at the school I attended and my first year of university, the sort where you remove "chads" with a pen (it was meant to be a paper clip)  and that sometimes got stuck and subsequently mangled in the card reader. Memories!

---

### Post by Krupski on 2010-05-22
Thread revisited. I *think* I found a "nice" way to structure the program... 

My goal was to do something like this:

for(start, end, ++) {

* If step 1 not OK, skip this file.
* If step 2 not OK, skip this file.
* If step 3 not OK, skip this file.
(made it through, process the file)

}

I think I got it right. Comments please:

```

///////////////////////////////////////////////////////////////////////////
//
// fixcr.c - Convert text to UNIX format,removes trailing spaces
// Copyright 2010 Roger A. Krupski <krupski@acsu.buffalo.edu>
//
// This program is free software: you can redistribute it and/or modify
// it under the terms of the GNU General Public License as published by
// the Free Software Foundation, either version 3 of the License, or
// (at your option) any later version.
//
// This program is distributed in the hope that it will be useful,
// but WITHOUT ANY WARRANTY; without even the implied warranty of
// MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
// GNU General Public License for more details.
//
// You should have received a copy of the GNU General Public License
// along with this program.  If not, see <http://www.gnu.org/licenses/>.
//
///////////////////////////////////////////////////////////////////////////

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>

#undef BUFSIZ
#define BUFSIZ 8192

int readln(FILE *, char *);
int checkexec(char *);
FILE *openfile(char *, int);
long int getfilesize(FILE *);
char *allocbuffer(long int);
long int readfile(FILE *, char *);
long int writefile(FILE * fp, char *);
int report(long int, char *);

int main(int argc, char *argv[])
{
	FILE *fp;
	char *buffer;
	long int n, count, insize, outsize;

	for (n = 1; n < argc; n++) {
		/* skip file if executable or dir */
		if (!(checkexec(argv[n]))) {
			break;
		}
		/* open for read */
		if (!(fp = openfile(argv[n], 0))) {
			break;
		}
		/* get original size */
		insize = getfilesize(fp);
		/* allocate memory for temp buffer */
		if (!(buffer = allocbuffer(insize))) {
			break;
		}
		/* read in and strip off junk */
		readfile(fp, buffer);
		/* open for write */
		if (!(fp = openfile(argv[n], 1))) {
			break;
		}
		/* write file & get bytes written */
		outsize = writefile(fp, buffer);
		/* de-allocate memory for temp buffer */
		free(buffer);
		/* in-out=how much was stripped off */
		report(insize - outsize, argv[n]);
	}
	return 0;
}

int readln(FILE * fp, char *str)
{
	char buf[BUFSIZ];
	int len, flag;
	buf[0] = 0;
	fgets(buf, BUFSIZ, fp);
	len = strlen(buf);
	flag = 0;
	while (len > -1) {
		if (buf[len] == 0x0A) {
			flag = 1;
		}
		if (buf[len] < 0x21) {
			buf[len] = 0;
			len--;
		} else {
			break;
		}
	}
	if (flag) {
		len++;
		buf[len] = 0x0A;
	}
	len++;
	buf[len] = 0;
	strncpy(str, buf, BUFSIZ);
	return strlen(str);
}

int checkexec(char *name)
{
	int result;
	result = access(name, X_OK);
	if (!result) {
		fprintf(stderr, "Skipping %s (exec or dir).\n", name);
	}
	return result;
}

FILE *openfile(char *name, int mode)
{
	FILE *fp = NULL;
	char *openmode[2] = { "rb", "wb" };
	char *openmsg[2] = { "read", "write" };
	if ((mode == 0) || (mode == 1)) {
		fp = fopen(name, openmode[mode]);
		if (fp == NULL) {
			fprintf(stderr, "Unable to open %s for %s.\n",
				name, openmsg[mode]);
		}
	}
	return fp;
}

long int getfilesize(FILE * fp)
{
	long int size;
	fseek(fp, 0L, SEEK_END);
	size = ftell(fp);
	fseek(fp, 0L, SEEK_SET);
	return size;
}

char *allocbuffer(long int size)
{
	long int x;
	char *buf = (char *)malloc(size + 1);
	if (buf == NULL) {
		fprintf(stderr,
			"Unable to allocate %ld bytes for buffer.\n", size);
	} else {
		for (x = 0; x < size + 1; x++) {
			buf[x] = 0;
		}
	}
	return buf;
}

long int readfile(FILE * fp, char *destin)
{
	long int len;
	char inbuf[BUFSIZ];
	while (!feof(fp)) {
		len = readln(fp, inbuf);
		strncat(destin, inbuf, len);
	}
	fclose(fp);
	return strlen(destin);
}

long int writefile(FILE * fp, char *source)
{
	fprintf(fp, "%s", source);
	fclose(fp);
	return strlen(source);
}

int report(long int size, char *name)
{
	fprintf(stdout, "%ld excess char%s removed from %s.\n", size,
		size == 1 ? "" : "s", name);
	return 0;
}

```

Thank you!

-- Roger

---

### Post by dwhitney67 on 2010-05-23
Krupski

From the code (and the comments within), I got the impression that the purpose of the application is to remove trailing non-white space characters from the end of a newline-terminated buffer.  If I misunderstood this, then forgive me.

Here's how I would have written the code:
```

#include <sys/stat.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <stdio.h>


int isExecutable(const int st_mode);
int isReadWritable(const int st_mode);

void fixFile(const char* filename);


int main(int argc, char** argv)
{
   if (argc == 1)
   {
      printf("Usage: %s <file1> [<file2> ... <fileN>]\n", argv[0]);
      return -1;
   }

   --argc; ++argv;

   while (argc-- != 0)
   {
      const char* filename = *argv++;
      struct stat buf;

      if (stat(filename, &buf) != 0)
      {
         fprintf(stderr, "Error, file '%s' not found.\n", filename);
         continue;
      }

      if (isExecutable(buf.st_mode))
      {
         fprintf(stderr, "Error, file '%s' is executable.\n", filename);
         continue;
      }

      if (!isReadWritable(buf.st_mode))
      {
         fprintf(stderr, "Error, file '%s' is not readable and/or writable.\n", filename);
         continue;
      }

      fixFile(filename);
      fprintf(stdout, "Fixed file '%s'\n", filename);
   }

   return 0;
}


int isExecutable(const int st_mode)
{
   return st_mode & (S_IXUSR | S_IXGRP | S_IXOTH);
}


int isReadWritable(const int st_mode)
{
   return (st_mode & (S_IRUSR | S_IRGRP | S_IROTH)) &&
          (st_mode & (S_IWUSR | S_IWGRP | S_IWOTH));
}


void fixFile(const char* filename)
{
   char tmpFilename[] = "fixcr_XXXXXX";

   int   desc  = mkstemp(tmpFilename);
   FILE* fptmp = fdopen(desc, "w");
   FILE* fp    = fopen(filename, "r");

   char buffer[8 * 1024] = {0};

   while (fgets(buffer, sizeof(buffer), fp))
   {
      char* ch = strchr(buffer, '\n');

      if (ch != buffer)
      {
         while (*(--ch) < 0x20);

         *(++ch) = '\n';
         *(++ch) = '\0';
      }

      fputs(buffer, fptmp);
   }

   fclose(fp);
   fclose(fptmp);

   unlink(filename);
   rename(tmpFilename, filename);
}

```

I have not fully tested the code above because I do not have a "corrupted" file such as the one you have in your environment.

---

