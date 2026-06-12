---
title: "malloc() question"
date: 2009-06-02
forum: Programming Talk
---

### Post by nmccrina on 2009-06-02
Hi, guys!

I'm trying to wrap my head around pointers and memory allocation. So I wrote this little test program.

```

#include <stdio.h>
#include <stdlib.h>

int main()
{	
	char *string;

	string = (char *)malloc(1);

	*string = 'k';
	*(string + 1) = 'z';
	printf("\n%c%c\n\n", *string, *(string + 1));

	free(string);

	return 0;
}

```

What I don't understand is why I don't get a segmentation fault when I try to read and write *(string + 1). Since I only allocated 1 byte with malloc(), shouldn't something somewhere be complaining? Or is this the kind of thing my mom warned me about with c, where it lets you do anything even if it has bad outcomes? :) I'm assuming that being able to access *(string + 1) is bad?

---

### Post by phrostbyte on 2009-06-02
What happens when you go out of memory bounds is sometimes unpredictable. Try + 10000 and see if you get a segfault. :D

---

### Post by lensman3 on 2009-06-02
> **nmccrina said:**
> Hi, guys!

I'm trying to wrap my head around pointers and memory allocation. So I wrote this little test program.

```

#include <stdio.h>
#include <stdlib.h>

int main()
{	
	char *string;

	string = (char *)malloc(1);

	*string = 'k';
	*(string + 1) = 'z';
	printf("\n%c%c\n\n", *string, *(string + 1));

	free(string);

	return 0;
}

```

What I don't understand is why I don't get a segmentation fault when I try to read and write *(string + 1). Since I only allocated 1 byte with malloc(), shouldn't something somewhere be complaining? 

No. Not in C.  The code to check for out of bounds would just slow down the program.  In your case you allocated one byte, then wrote a 'z' outside of the malloc'ed area.  

There are add one packages that will warn you of memory leakage and overwrites.  These packages should be used during development but shouldn't be in the release.  


> Or is this the kind of thing my mom warned me about with c, where it lets you do anything even if it has bad outcomes? :) I'm assuming that being able to access *(string + 1) is bad?

Yes.  If you used 

printf( %s, string );

This would failing because the string was not null terminated.  M$ is currently pushing the cause that memcpy should never be used in secure programs.  The problem is the third argument which is the length of the destination buffer.  The problem is that "stupid" programmers pick a too small of destination buffer.  Problems should be picked up by a program called "lint" or gcc "verbose" and warn you of a possible problem.  

Take a look at gets() and the problems it has.

---

### Post by lisati on 2009-06-02
I wouldn't advocate eliminating "sanity" checks altogether. In simple programs careful coding will help avoid 99.9% of the problems that are likely to crop up, which is near enough to 100% that it won't usually cause a problem. It's in the larger programs where the previously negligible chance of problems like a segmentation fault or memory leak get magnified.

And yes, I agree, taking care to ensure that destination buffers are big enough is a good idea.

<nostalgic rant>On one of the machines I used back in the 1980s, people who ran software usually needed to give the OS instructions that related the "logical file name" used in a program ("ddname" is what they called it) to a real file (or group of files) prior to running the software. If such an instruction was omitted, the open would fail, and if the programmer hadn't put in suitable error handling, the results could be spectacular when the program tried to read from the file: an error message that suggested an "invalid opcode" and a massive core dump. The silly thing was that in ASM, you could have one line of code that would check if the "open file" worked, and another line of code to redirect the program to a "die gracefully" routine if it didn't....As far as I'm aware, the COBOL compiler used by some of my colleagues didn't use this simple trick.</nostalgic rant>

---

### Post by crdlb on 2009-06-02
This isn't really related to your question, but I feel like pointing out a couple of style issues:[LIST]
[*]Don't cast malloc's return value, since void* implicitly converts to any pointer type (except in C++, where you shouldn't use malloc anyway)
[*]Use string[0] and string[1] instead of *string and *(string + 1). Those are precisely equivalent, but this is the convention when using strings and other arrays. The only time I'd use * with an array is when using a while loop and incrementing the pointer (ptr[0] would be misleading in that case since it's not at the start of the array)
[/LIST]

---

### Post by Can+~ on 2009-06-02
Be thankful when your program has a segfault, the biggest annoyance is when you are stepping out of your reserved space and no one told you.

I once saw a simple exercise made by a student that failed because he accidentally wrote a char(2); where a 2-lettered word (and it's \n) was stored, and the remaining '\n' landed on another variable on another different scope, leading to some weird results.

---

### Post by nmccrina on 2009-06-02
> **lensman3 said:**
> No. Not in C.  The code to check for out of bounds would just slow down the program.

That makes sense. Thanks! :D

---

### Post by nmccrina on 2009-06-02
> **crdlb said:**
> This isn't really related to your question, but I feel like pointing out a couple of style issues:[LIST]
[*]Don't cast malloc's return value, since void* implicitly converts to any pointer type (except in C++, where you shouldn't use malloc anyway)
[*]Use string[0] and string[1] instead of *string and *(string + 1). Those are precisely equivalent, but this is the convention when using strings and other arrays. The only time I'd use * with an array is when using a while loop and incrementing the pointer (ptr[0] would be misleading in that case since it's not at the start of the array)
[/LIST]

Alright. I've seen the malloc return value done both ways around the internet. Thanks for clarifying.

---

### Post by lensman3 on 2009-06-02
Take a look at

[http://c-faq.com/decl/strlitinit.html](http://c-faq.com/decl/strlitinit.html)


The c-faq.com site has a good section on character strings.

---

### Post by NathanB on 2009-06-03
This should be helpful:

[http://www.eternallyconfuzzled.com/tuts/languages/jsw_tut_pointers.aspx](http://www.eternallyconfuzzled.com/tuts/languages/jsw_tut_pointers.aspx)

---

### Post by slavik on 2009-06-03
> **crdlb said:**
> This isn't really related to your question, but I feel like pointing out a couple of style issues:[LIST]
[*]Don't cast malloc's return value, since void* implicitly converts to any pointer type (except in C++, where you shouldn't use malloc anyway)
[*]Use string[0] and string[1] instead of *string and *(string + 1). Those are precisely equivalent, but this is the convention when using strings and other arrays. The only time I'd use * with an array is when using a while loop and incrementing the pointer (ptr[0] would be misleading in that case since it's not at the start of the array)
[/LIST]
I would disagree on the first point (I am of the explicitness camp).
On the second point ... IMO, either way is fine, but if you have a pointer inside of an array, ie: int array[]; int* ptr; then the pointer would point to a specific value in what I consider better style. As in ptr=&(array[3]); *ptr == array[3] //this is true.

---

### Post by Arndt on 2009-06-03
> **nmccrina said:**
> Hi, guys!

I'm trying to wrap my head around pointers and memory allocation. So I wrote this little test program.

```

#include <stdio.h>
#include <stdlib.h>

int main()
{	
	char *string;

	string = (char *)malloc(1);

	*string = 'k';
	*(string + 1) = 'z';
	printf("\n%c%c\n\n", *string, *(string + 1));

	free(string);

	return 0;
}

```

What I don't understand is why I don't get a segmentation fault when I try to read and write *(string + 1). Since I only allocated 1 byte with malloc(), shouldn't something somewhere be complaining? Or is this the kind of thing my mom warned me about with c, where it lets you do anything even if it has bad outcomes? :) I'm assuming that being able to access *(string + 1) is bad?

The address string+1 is probably in the same memory word as string. The allocation of one byte will have actually allocated four or eight bytes.

---

### Post by alternatealias on 2009-06-04
> **slavik said:**
> I would disagree on the first point (I am of the explicitness camp).

The problem with casting the return value of malloc() (and other void*-returning functions) is that it masks potential problems as far as including the proper headers (or defining the proper prototypes).

Most C compilers, if the function hasn't already been defined, will make (sometimes wrong) assumptions about the return-type (usually assume int) and sometimes argument types of functions.

The reason functions return void* is so that you don't /have/ to cast.

---

