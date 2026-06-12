---
title: "How to change one character in a string array"
date: 2009-11-04
forum: Programming Talk
---

### Post by stefangr1 on 2009-11-04
I have a question regarding string arrays. I realize the answer is probably pretty straightforward, but I couldn't find it in the C-book I have or on Google (or in the FAQ).

I don't understand why changing one letter in a string array (like in the example below) is allowed when the array was filled byte for byte, but not when it was filled like: text = "text". Also, if I copy one array into another one, comparing them always result in a FALSE. Can someone explain me what the difference is, and how I can modify / compare string arrays?


#include <stdlib.h>
#include <stdio.h>

#define SIZE 14

int main()
{
	char *text; int i;

        [COLOR="DarkRed"]/* Method I to initialize a string array */[/COLOR]
	text = malloc(SIZE * sizeof(char));
	text = "Hello, world!";
	printf("%s\n", text);
	for(i = 0; i < SIZE; i++) printf("%02x ", text[i]); printf("\n\n");

	char *text2;
	text2 = malloc(SIZE * sizeof(char));

        [COLOR="DarkRed"]/* When I copy the string aray to another aray, they LOOK the same, but in fact they're NOT the same, I don't understand why... */[/COLOR]
	memcpy(text2, text, SIZE * sizeof(char));
	printf("%s\n", text2);
[COLOR="DarkRed"]/* The statement below always results 0, even though memcpy was used to duplicate the array. */[/COLOR]
	printf("Are they the same?: %d\n", text == text2);

[COLOR="DarkRed"]/* The same happens whey I copy the string array like below */[/COLOR]
	for(i = 0; i < SIZE; i++) text2[i] = text[i];
	printf("%s\n", text2);
	printf("Are they the same?: %d\n", text == text2);

[COLOR="DarkRed"]        /* Even though the arrays look the same. */[/COLOR]
	for(i = 0; i < SIZE; i++) printf("%02x ", text[i]); printf("\n");

[COLOR="DarkRed"]/* Here changing one character works as I would expect. */[/COLOR]
	text2[0] = (char)'A';
	for(i = 0; i < SIZE; i++) printf("%02x ", text2[i]); printf("\n");

        [COLOR="DarkRed"]/* This is where the program crashes... */[/COLOR]
	text[0] = (char)'A';
	for(i = 0; i < SIZE; i++) printf("%02x ", text[i]); printf("\n");

	return 0;
}

---

### Post by froggyswamp on 2009-11-04
As a side note I'd suggest creating code that supports/works with UTF ( 8 ), doing pure ascii stuff is nowadays mostly not welcome.

---

### Post by stefangr1 on 2009-11-05
> **froggyswamp said:**
> As a side note I'd suggest creating code that supports/works with UTF ( 8 ), doing pure ascii stuff is nowadays mostly not welcome.

OK, but that's a little off topic. No one can allocate a few seconds to have a look at this question?

---

### Post by Arndt on 2009-11-05
> **stefangr1 said:**
> I have a question regarding string arrays. I realize the answer is probably pretty straightforward, but I couldn't find it in the C-book I have or on Google (or in the FAQ).

I don't understand why changing one letter in a string array (like in the example below) is allowed when the array was filled byte for byte, but not when it was filled like: text = "text". Also, if I copy one array into another one, comparing them always result in a FALSE. Can someone explain me what the difference is, and how I can modify / compare string arrays?


#include <stdlib.h>
#include <stdio.h>

#define SIZE 14

int main()
{
	char *text; int i;

        [COLOR="DarkRed"]/* Method I to initialize a string array */[/COLOR]
	text = malloc(SIZE * sizeof(char));
	text = "Hello, world!";
	printf("%s\n", text);
	for(i = 0; i < SIZE; i++) printf("%02x ", text[i]); printf("\n\n");

	char *text2;
	text2 = malloc(SIZE * sizeof(char));

        [COLOR="DarkRed"]/* When I copy the string aray to another aray, they LOOK the same, but in fact they're NOT the same, I don't understand why... */[/COLOR]
	memcpy(text2, text, SIZE * sizeof(char));
	printf("%s\n", text2);
[COLOR="DarkRed"]/* The statement below always results 0, even though memcpy was used to duplicate the array. */[/COLOR]
	printf("Are they the same?: %d\n", text == text2);

[COLOR="DarkRed"]/* The same happens whey I copy the string array like below */[/COLOR]
	for(i = 0; i < SIZE; i++) text2[i] = text[i];
	printf("%s\n", text2);
	printf("Are they the same?: %d\n", text == text2);

[COLOR="DarkRed"]        /* Even though the arrays look the same. */[/COLOR]
	for(i = 0; i < SIZE; i++) printf("%02x ", text[i]); printf("\n");

[COLOR="DarkRed"]/* Here changing one character works as I would expect. */[/COLOR]
	text2[0] = (char)'A';
	for(i = 0; i < SIZE; i++) printf("%02x ", text2[i]); printf("\n");

        [COLOR="DarkRed"]/* This is where the program crashes... */[/COLOR]
	text[0] = (char)'A';
	for(i = 0; i < SIZE; i++) printf("%02x ", text[i]); printf("\n");

	return 0;
}

A number of comments:

* text == text2, this compares the values of the strings, as pointers. They may very well be equal in that they contain the same characters, but here the addresses to the strings are compared. Use strcmp to compate the contents.

* (char)'A'  the cast is not needed - 'A' is already a char.

* You first malloc some memory and let text point to it, then immediately set text to a literal string instead. This does not have the effect of filling the allocated area with the string - it gives text a new value and throws away the malloced string (but doesn't free it - it just lies there). Use strcpy to copy strings.

I haven't tried to run your program, but if at some point you happen to try to replace a character in a literal string, the program may crash, because the compiler is allowed to put the literals in read only memory.

sizeof(char) is also sort of unnecessary - it's always 1 - but some people use it to make it clear what is being allocated.

---

### Post by samjh on 2009-11-05
> **stefangr1 said:**
> 
	char *text; int i;

        [COLOR="DarkRed"]/* Method I to initialize a string array */[/COLOR]
	text = malloc(SIZE * sizeof(char));
	text = "Hello, world!";

Wrong usage.  The last line quoted should be:

```
strcpy(text, "Hello, world!");
```

If you use a string constant to initialise a character pointer, it will be read-only.  If you want to be able to modify a string, you need to use either **text[] = "Hello, world!";** or use the strcpy function on the pointer to the string.

---

### Post by dwhitney67 on 2009-11-05
> **samjh said:**
> Wrong usage.  The last line quoted should be:

```
strcpy(text, "Hello, world!");
```

If you use a string constant to initialise a character pointer, it will be read-only.  If you want to be able to modify a string, you need to use either **text[] = "Hello, world!";** or use the strcpy function on the pointer to the string.

And better yet, strncpy() should be used so that the size of the area pointed to by 'text' can be conveyed.
```

strncpy(text, "Hello, world!", SIZE-1);

```

---

### Post by stefangr1 on 2009-11-05
Thanks a lot! The comments were all very insightful, and I know enough now to apply this in the program I'm making. Just reading a C book or tutorial doesn't give this type of information (like that the string was written to write only memory in my first program). I should have know about comparing the pointers though :oops: .

---

### Post by johnl on 2009-11-05
> **dwhitney67 said:**
> And better yet, strncpy() should be used so that the size of the area pointed to by 'text' can be conveyed.
```

strncpy(text, "Hello, world!", SIZE-1);

```

I think that you would want:

```

strncpy(text, "Hello, world!", SIZE);
text[SIZE - 1] = '\0';

```

otherwise if the string you are copying to text happens to be exactly SIZE-1 characters long your result will not be null terminated, although it would have been able to fit in the buffer.

if your string is longer than SIZE your result will not be null terminated.

---

