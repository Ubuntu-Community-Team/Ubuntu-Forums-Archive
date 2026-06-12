---
title: "character arrays in C"
date: 2010-11-03
forum: Programming Talk
---

### Post by jamesbon on 2010-11-03
I was reading Kernighan Ritchie book chapter 4 which deals with character pointers.
I am not able to understand  following different type of declarations

```
char aname[][15] = { "Illegal month", "Jan", "Feb", "Mar" };
char amessage[] = "now is the time"; 
char *name[] = { "Illegal month", "Jan", "Feb", "Mar" };

```
What is the difference between these three?

---

### Post by worksofcraft on 2010-11-03
> **jamesbon said:**
> I was reading Kernighan Ritchie book chapter 4 which deals with character pointers.
I am not able to understand  following different type of declarations

```
char aname[][15] = { "Illegal month", "Jan", "Feb", "Mar" };
char amessage[] = "now is the time"; 
char *name[] = { "Illegal month", "Jan", "Feb", "Mar" };

```
What is the difference between these three?

The first one sets asidean area of memory that is 4 rows of 15 bytes each and initializes each row with the given text.

The second one creates a single array of 16 bytes and initializes it with the text.

The last one creates an array of 4 pointers and initializes each of those pointers to point to the strings.

printing their sizes may shed further light on this ...
[php]
printf("sizeof(aname)=%lu, sizeof(amessage)=%lu, sizeof(name)=%lu\n",
sizeof(aname), sizeof(amessage), sizeof(name));
[/php]

You know I think there is a need for some simple C/C++ tutorials on the web. I can invisage this chapter: "pointers and arrays... where is it stored?"

---

### Post by Arndt on 2010-11-03
> **worksofcraft said:**
> The first one sets asidean area of memory that is 4 rows of 15 bytes each and initializes each row with the given text.

The second one creates a single array of 16 bytes and initializes it with the text.

The last one creates an array of 4 pointers and initializes each of those pointers to point to the strings.

printing their sizes may shed further light on this ...
[php]
printf("sizeof(aname)=%lu, sizeof(amessage)=%lu, sizeof(name)=%lu\n",
sizeof(aname), sizeof(amessage), sizeof(name));
[/php]

You know I think there is a need for some simple C/C++ tutorials on the web. I can invisage this chapter: "pointers and arrays... where is it stored?"

It helps a lot to draw little boxes and arrows on paper. Some books already use these boxes and arrows when explaining the concepts.

---

### Post by gmargo on 2010-11-03
Do yourself a favor and install the **cdecl** package.

```

$ cdecl explain "char aname[][15]"
declare aname as array of array 15 of char

$ cdecl explain "char amessage[]"
declare amessage as array of char

$ cdecl explain "char *name[]"
declare name as array of pointer to char

```

---

### Post by spjackson on 2010-11-03
> **jamesbon said:**
> I was reading Kernighan Ritchie book chapter 4 which deals with character pointers.

An excellent decision. I hope this is the ANSI C version which describes what became the ISO C standard in 1989. The chapter you mention (chapter 5?) describes very clearly the difference between the 1st and 3rd definition by means of an excellent diagram.

---

### Post by jamesbon on 2010-11-04
Ok from Chapter 5 section 5.3 page 81 says 
```
"Any operation that can be achieved by array
subscripting can also be done with pointers."

```> **worksofcraft said:**
> The first one sets asidean area of memory that is 4 rows of 15 bytes each and initializes each row with the given text.

The second one creates a single array of 16 bytes and initializes it with the text.

Ok clear upto here

> **worksofcraft said:**
> 
The last one creates an array of 4 pointers and initializes each of those pointers to point to the strings. printing their sizes may shed further light on this ...

This is what I want to know what is the difference between array of pointers and a character array.
Is 
```
char aname[15]
```not same as 
```
char *aname
```Since the name of an array is a synonym for the location of the initial element,
In both the cases we will access the values stored in these arrays in same way.

```

char *name[] = { "Illegal month", "Jan", "Feb", "Mar" };

```
So can I access the members of the above declaration as

name[0][2] should give me l
and 
name [2][0] should have F


> **worksofcraft said:**
> 
You know I think there is a need for some simple C/C++ tutorials on the web. I can invisage this chapter: "pointers and arrays... where is it stored?"


Page number 87 onwards of Kernighan Ritchie has this from there my confusion started 

Actually I am not able to understand that what is the difference between array of character pointers and character array.

Is there a way I can quote the replies of many people in a message if I have to quote all the replies above I have to click on quote button and copy paste the string that begins with [quote= and then like this copy multiple messages and then do editing of that to be able to answer.

when a character array is declared the array name is refers to

---

### Post by worksofcraft on 2010-11-04
> **jamesbon said:**
> ...
This is what I want to know what is the difference between array of pointers and a character array.
Is 
```
char aname[15]
```not same as 
```
char *aname
```Since the name of an array is a synonym for the location of the initial element,
In both the cases we will access the values stored in these arrays in same way.


yes the name of the array is synonymous with the location of the first element... but following that location you have also told the compiler to reserve a further 15 locations to hold more data.

The pointer can also hold the memory address of that first location... but  it still needs a valid location to point to.

Now the difference between a pointer and the name of the array is that the name of the array is given a constant known and unchangeable memory address while the pointer is itself stored in memory and can be changed to point to different things. Brb I'll write a little example.

---

### Post by worksofcraft on 2010-11-04
[php]

#include <stdio.h>

int main() {
	const char string1[] = "string1";
	const char string2[] = "string2";
	const char *stringptr = "stringpointer";

	// Now I've declared them "const" that, means that  it will be an error to try
	// and change the strings... so now we can be confident that they won't get changed.
	// let us see where they are stored.
	printf("string1=%p, string2=%p, stringptr=%p\n", string1, string2, stringptr);
	printf("1=%s, 2=%s, 3=%s\n", string1, string2, stringptr);
	// however we can change the pointer to point somwehere else:
	stringptr = string1; // change where it points to
	printf("string1=%p, string2=%p, stringptr=%p\n", string1, string2, stringptr);
	printf("1=%s, 2=%s, 3=%s\n", string1, string2, stringptr);
	// did you see how stringpointer has changed to now point to the location of string1?

	// another thing to notice is that the pointer itself is stored in memory and
	// You can see where it is as follows:
	printf("the location where stringptr is stored is %p\n", &stringptr);
	return !"to sender... address unknown!";

}
[/php]

OTOH if you try to change string1 or string2 you will get a compiler error, because these are memory addresses are calculated at compile time and so they can't be changed: they are fixed and built into the actual instructions that the compiler has generated :shock:

---

