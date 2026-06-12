---
title: "Get size of string? (not what you think!)"
date: 2009-12-05
forum: Programming Talk
---

### Post by Krupski on 2009-12-05
Hi all,

I have a small function that I use for line reading from STDIN or from files.

Anyway, I decided to modify the function so that instead of using a hard coded buffer size, it would dynamically allocate the space required.

It works except I ran into one snag that I can't seem to figure out (see code below).

If I manually set 'n' to a number, it works. But what I WANT to do is get the size of the incoming buffer ('str') and use that instead.

I tried "strlen(str)" and "sizeof(str)" then sat back and laughed at myself for my foolishness... then I realized that I don't know HOW to determine what size has been allocated for 'str'.

So, oh *kind* and *wise* gurus of the C programming language... what the heck should I do?

Thanks!!!

-- Roger

```

// read a line from "file" and return the string with any
// carriage return or linefeed removed, null terminated.
// also return the numeric value of the input if it's
// numeric and 1, 0 or -1 for yes/no/failed

int readln(FILE *fp, long double *dnum, long int *inum, char ***[COLOR="Red"]str[/COLOR]**)
{
	[B][COLOR="Red"]int n = ??????????????; // here is the problem
	// what I WANT to do is this:
	// int n = allocated_size_of(str);[/COLOR][/B]

	char *buf = (char*)malloc(n);

	if (buf == NULL) { return -1; }

	buf[0] = 0; // initialize buffer in case of no input

	fgets(buf, n, fp); // read data into buffer

	n = strlen(buf);

	while(n >= 0) { // remove trailing junk from line
		if(buf[n] <= 0x20) { buf[n] = 0; n--; }
		else { break; }
	}

	n++; // account for the null needed at the end

	buf[n] = 0;

	strcpy(str, buf); // copy temp buffer to caller's string

	*dnum = atof(buf); // get floating point value

	*inum = (long int)(*dnum < 0 ? *dnum - 0.5 : *dnum + 0.5); // get symmetric rounded int value

	sscanf(buf, "%s", buf); // remove leading spaces, if any, from buffer

	n = (buf[0] == 'Y' || buf[0] == 'y'); // set 'n' based on the first character in buffer

	free(buf); // de-allocate temp buffer

	return n;
}

```

---

### Post by MadCow108 on 2009-12-05
if you are reading from a stream there is no way to determine the buffer size beforehand as you don't know when a stream stops.

so the easy way:
use getline/getdelim (gnu extension, not portable)
they handle the allocation for you

a bit more work: repeatedly read stuff with fgets into a fixed size buffer and after each fgets concatenate that into your final dynamic buffer

if you are reading from a file use fseek to determine the filesize and allocate appropriately

---

### Post by Krupski on 2009-12-05
> **MadCow108 said:**
> if you are reading from a stream there is no way to determine the buffer size beforehand as you don't know when a stream stops.


No... what I want to know is the size of the buffer who's pointer is passed to my function.

For example, if I do this:

```

    char buffer[1024];

    readln(stdin, &dnum, &inum, buffer);
    .......

```

You see that the buffer which readln() has to work with is 1024 bytes. So, I want readln() to "know" the size of the buffer, allocate accordingly, do it's thing, then free and return.

In main() I know that my buffer is 1024 bytes, but when I pass it to readln(), the function doesn't know the buffer size... and that's what I'm trying to figure out how to determine.

-- Roger

---

### Post by dwhitney67 on 2009-12-05
There is no way... unless you pass along the size of the buffer to the function.


P.S.  In your copious spare time, read the manpage on gets().  It's a favorite catch for IA weenies.

---

### Post by Krupski on 2009-12-05
> **dwhitney67 said:**
> There is no way... unless you pass along the size of the buffer to the function.


P.S.  In your copious spare time, read the manpage on gets().  It's a favorite catch for IA weenies.

Well, I guess "there is no way" kinda solves this post!  :)

By the way, what is an "IA weenie"?

(edit to add): I think I have fgets() pretty much figured out. Your statement about reading the manpage for it suggests that I used it incorrectly. If so please elaborate?

---

### Post by LKjell on 2009-12-05
> **Krupski said:**
> Well, I guess "there is no way" kinda solves this post!  :)

By the way, what is an "IA weenie"?

(edit to add): I think I have fgets() pretty much figured out. Your statement about reading the manpage for it suggests that I used it incorrectly. If so please elaborate?

Well it was gets not fgets. Anyway

>        fgets() reads in at most one less than size characters from stream  and
       stores  them  into  the buffer pointed to by s.  Reading stops after an
       EOF or a newline.  If a newline is read, it is stored into the  buffer.
       A '\0' is stored after the last character in the buffer.


Therefore
```
	while(n >= 0) { // remove trailing junk from line
		if(buf[n] <= 0x20) { buf[n] = 0; n--; }
		else { break; }
	}

```
Is just waste of space. And you need to put fgets in a loop. And at least two buffer string to be safe. One dynamic and one static. Or just two dynamics.

Another question is what you mean by size of string. Is it size of allocated memory or total amount of characters? See memcpy and strcpy to get the idea.

---

### Post by Krupski on 2009-12-05
> **LKjell said:**
> Well it was gets not fgets. Anyway



Therefore
```
	while(n >= 0) { // remove trailing junk from line
		if(buf[n] <= 0x20) { buf[n] = 0; n--; }
		else { break; }
	}

```
Is just waste of space. And you need to put fgets in a loop. And at least two buffer string to be safe. One dynamic and one static. Or just two dynamics.

Another question is what you mean by size of string. Is it size of allocated memory or total amount of characters? See memcpy and strcpy to get the idea.

The reason I have the "trailing junk" removal code in there is because when I read a string from a file, I want it to be "clean". For example, in Linux reading a text file I would get this (each parentheses represents a character and CR or LF are obvious):


In Linux:
```

(H)(e)(l)(l)(o)( )(T)(h)(e)(r)(e)(LF)(\0)

```

In DOS/Windows, I would get this:
```

(H)(e)(l)(l)(o)( )(T)(h)(e)(r)(e)(CR)(LF)(\0)

```

On a MAC I would get this:
```

(H)(e)(l)(l)(o)( )(T)(h)(e)(r)(e)(CR)(\0)

```

My code removes all the junk and yields a consistent result:
```

(H)(e)(l)(l)(o)( )(T)(h)(e)(r)(e)(\0)

```

Then I can use the string as-is for fopen(), or I can add newlines to it if I want... point it I get CONSISTENT results when cross compiling the code on different machines.

To answer your other question, what I wanted to know was the allocated size of the buffer that was passed to my function. If, in main() it was declared as "char buffer[1024];", I want to get that "1024" somehow.

That way, when I use fgets(), I'll never read more into the buffer than it can hold.

The real reason I'm doing this is I'm S-L-O-W-L-Y teaching myself and "malloc()" was next on my list of things to figure out, so I tried to put it to use in an experimental piece of code that I had already written.

But, I've already been told that it can't be done, so I guess it can't... ?

-- Roger

---

### Post by Krupski on 2009-12-05
> **LKjell said:**
> And you need to put fgets in a loop.

I don't need it in a loop because I'm expecting to read only one line at a time (and the "lines" are text).

---

### Post by LKjell on 2009-12-06
The context of dynamic memory is kinda misused here. To solve your problem is to pass the memory size to the function. Obvious you know the size when you initiate char buffer[1024] in main().

And about the LF... you could just do 	```
n = strlen(buf);

if(buf[n-1] == '\n')
        buf[n-1] = '\0';
```

Of course if you do not find a newline you have to do fgets again. That is what I was referring to have two buffer.

---

### Post by TennTux on 2009-12-07
> **Krupski said:**
> No... what I want to know is the size of the buffer who's pointer is passed to my function.

For example, if I do this:

```

    char buffer[1024];

    readln(stdin, &dnum, &inum, buffer);
    .......

```

You see that the buffer which readln() has to work with is 1024 bytes. So, I want readln() to "know" the size of the buffer, allocate accordingly, do it's thing, then free and return.

In main() I know that my buffer is 1024 bytes, but when I pass it to readln(), the function doesn't know the buffer size... and that's what I'm trying to figure out how to determine.

-- Roger

Alright. It may be possible to get the size, however, you can not get the size of a "char *". This is just a pointer to one or more char and you can't know what was allocated outside the function. You can get the size of buffer[1024] in the main function with the sizeof(buffer) and pass it into the function.

This would make your call something like:
```

readln(stdin, &dnum, &inum, buffer, sizeof(buffer));

```

Though you should be careful. sizeof(buffer) gives you the number of bytes and if that is what you need, great. However, if you need the number of elements in the array, which may be the case if your code needs to handle both ASCII and UNICODE, then you may need to use something like:
```
 
#if defined(UNICODE)
typedef wchar CharType ;
#else
typedef char CharType ;
#endif
CharType  buffer[1024] ;
int buffer_size = sizeof(buffer)/sizeof(CharType)

```

---

### Post by MadCow108 on 2009-12-07
> **TennTux said:**
> 
```
 
#if defined(UNICODE)
typedef wchar CharType ;
#else
typedef char CharType ;
#endif
CharType  buffer[1024] ;
int buffer_size = sizeof(buffer)/sizeof(CharType)

```
you can also just write:
sizeof(array)/sizeof(array[0])
(of course only if array is an array and no pointer!, beware of implicit conversion)

and the return type of sizeof is size_t and not int!

---

### Post by TennTux on 2009-12-07
> **Krupski said:**
> ...
The real reason I'm doing this is I'm S-L-O-W-L-Y teaching myself and "malloc()" was next on my list of things to figure out, so I tried to put it to use in an experimental piece of code that I had already written.
...

If your point is to learn malloc you may want code something like this:
```
#declare BUFF_SIZE 1024

// Since sizeof(char) = 1 then buff_size = BUFF_SIZE
int buff_size = BUFF_SIZE * sizeof(char) ;
char* buffer = malloc(buff_size) ;
readln(stdin, &dnum, &inum, buff_size) ;
free(buffer) ;
```

---

### Post by dwhitney67 on 2009-12-07
> **TennTux said:**
> If your point is to learn malloc you may want code something like this:
```
#declare BUFF_SIZE 1024

// Since sizeof(char) = 1 then buff_size = BUFF_SIZE
int buff_size = BUFF_SIZE * sizeof(char) ;
char* buffer = malloc(buff_size) ;
readln(stdin, &dnum, &inum, buff_size) ;
free(buffer) ;
```

You lost me with this post?  What's the point of declaring and allocating memory for 'buffer'?  What is 'dnum' and 'inum'?

If you examine the manpage for malloc(), you will notice that it takes a parameter of type size_t.  Although an int is usable (as you have shown above), it is not the proper data type to use.

---

### Post by wmcbrine on 2009-12-07
> **Krupski said:**
> For example, in Linux reading a text file I would get this (each parentheses represents a character and CR or LF are obvious):


In Linux:
```

(H)(e)(l)(l)(o)( )(T)(h)(e)(r)(e)(LF)(\0)

```

In DOS/Windows, I would get this:
```

(H)(e)(l)(l)(o)( )(T)(h)(e)(r)(e)(CR)(LF)(\0)

```Actually, if you open a (native) text file in text mode -- the default -- then the lines should end in '\n' (LF) on every platform.

Also:

> [i]
On a MAC I would get this:
```

(H)(e)(l)(l)(o)( )(T)(h)(e)(r)(e)(CR)(\0)

```[/i]The CR-only line endings are deprecated in Mac OS X, in favor of Unix-style endings (LF only). Although apparently there are still a few Mac apps that haven't heard the news.

---

### Post by TennTux on 2009-12-09
> **dwhitney67 said:**
> You lost me with this post?  What's the point of declaring and allocating memory for 'buffer'?  What is 'dnum' and 'inum'?

If you examine the manpage for malloc(), you will notice that it takes a parameter of type size_t.  Although an int is usable (as you have shown above), it is not the proper data type to use.

When I made the post I quoted Krupski the originator of this discussion who said
> 
...
The real reason I'm doing this is I'm S-L-O-W-L-Y teaching myself and "malloc()" was next on my list of things to figure out, so I tried to put it to use in an experimental piece of code that I had already written.
...


So if Krupski was trying to learn how to use malloc and was creating a place to use malloc in their existing code, I was trying to show them a possible way to do it.

As for the point about int verses size_t. Ok. I responded quickly and didn't check the parameter type. But the concept of allocation, use and deallocation was there.

And finally as for the dnum and inum those make sense in the context of Krupski's code sample that occured in the post I took the statement from.

I hope this clarifys all your concerns. Sometimes people that put their issues out there are looking for someone to guide or help them in the right direction rather than having someone get in their face.  I M [H] O.

---

