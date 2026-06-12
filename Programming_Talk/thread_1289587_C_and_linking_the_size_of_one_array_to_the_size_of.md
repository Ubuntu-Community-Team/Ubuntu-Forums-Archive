---
title: "C and linking the size of one array to the size of another one"
date: 2009-10-12
forum: Programming Talk
---

### Post by rbaleksandar on 2009-10-12
Hi, guys. :)

  Well, I've started making a project of mine written in C. I'm still learning so please not too fancy stuff. :) Here's the deal...But first to mention that I use GCC (it might have something to do with my problem...perhaps ;)).

  I want to define 2 string (one dim. arrays in C). The first one is a non-fixed-size array that is:
```
char array1[] = "hello"
```

  Then I define the second array with:
```
char array2[strlen(array1)+1]
```

  It takes the size of the array. I think it's possible but I'm not so sure since the array where I take the size of the second one is actually non-fixed-size and yet I define a start-value of array1, which is "hello" (length = 6 with the NULL at the end). So when I initialize the first array, it's been given a temporary size of 5 (NULL isn't counted when you call the array with strlen())... I think it works like that at least. :D
  I presume that my thoughts are correct and continue my story. ;) Now the problem is that when I call strlen() for both arrays I get cr*p (apologize for the expression but I feel it that way):

```


printf("%d", strlen(array1));      //returns 5, which is correct
printf("%d", strlen(array2));      //returns 3

```

  You see where the problem is...The evil 3. Ok, I suppose the code sucks and it's wrong and yet - where the hell does this 3 come from?! Even if I define my array2 with ```
char array2[strlen(array1) + 1000000000]
``` it returns 3. :confused:

  I want that in my program the first array is predefined and the second to be "dynamic" and fill it with as many characters as the first one.
  I tried to make array1 with a fixed size of 6 (hello is 5 characters + 1 characters for the NULL) and still the damn length of array2 is 3. :(

Would appreciate if someone can explain this mystery (at least for that's what it is :)).

Thanks in advance!

---

### Post by Habbit on 2009-10-12
This may sound a bit weird, but... have you actually filled the second array with data? If you haven't, then strlen is looking at the "random" data which happens to be in the place that your array now occupies.

---

### Post by fct on 2009-10-12
The length of a string (strlen) is not the same as the size of an array in C.

Since you haven't filled array2 with data, it seems like the uninitialized memory holds a string terminator at that position.

Also you should consider separate vars for the size of a char array and the length of the string, since you can have a [256] char array containing only the "hello" string with a length of 5.

---

### Post by rbaleksandar on 2009-10-12
**Habbit**, I fill my array later in the programm.
**fct**, I know - sizeof() and strlen() are totally different things and still I don't get it where this **3** comes from. Ok, array2 has no content. So following should happen:
```

sizeof(array2) = 1 //NULL's included
strlen(array2) = 0 //NULL's not included

```
  

  Oh, well, I got it up and running after all. :P I was stupid to forget of the wonderful **strcat()**. :popcorn:

Example:
```

#include <stdio.h>
#include <string.h>

int main(){
	char word[] = "Ubuntu";
	int wordSize = sizeof(word);
	char temp[] = "";
	int i;
	
	for(i=0; i<strlen(word); i++) strcat(temp, "-");
	printf("\n %s", temp);
	
	return 0;
}

```

  One last question - if I have the line ```
	int wordSize = sizeof(word);
```, this piece of code displays a correct result (that is 6 dashes) on the screen. The moment I delete it, I get only one. :confused:

---

### Post by MadCow108 on 2009-10-12
you get 3 because the array is filled with random garbage data, probably the position 3 is by chance 0 so you get 3

also the second array is not as dynamic as you think
its just an very unfortunate implementation of a static array
a better implementation would be:
```

char ar1[] = "blabla";
char ar2[sizeof(ar1)/sizeof(ar1[0])]; // ar2 has now same size as ar1 but its still empty!

``` 

sizeof is a compile time operation (so don't use on dynamic arrays!), so no runtime penalty compared to strlen (which is a O(N) operation) [the compiler could probably figure that out by itself but I wouldn't rely on that]

edit concerning new post:
```
char temp[] = "";
	int i;
	
	for(i=0; i<strlen(word); i++) strcat(temp, "-");
	printf("\n %s", temp);

```
the first line declares a size one char containing null
so you're operations on this array are buffer overruns!
C arrays do not grow automatically. You need do allocate enough memory to hold your buffers or let them grow manually (e.g. by realloc) when they exceed the size

sizeof returns the size of the data type, only in case of arrays this is equivalent to the array size. But if that array decays into a pointer (happens when you pass it into functions) sizeof will return the size of the pointer!
you have to be well aware of what this operator does, or you'll use it wrong

---

### Post by rbaleksandar on 2009-10-12
Thanks a lot for the explanation! :)

  Yes, you're right about all and mostly about the buffer-thingie. Have to forget about the dynamic arrays in Java. :P


Thanks again! Have to read more about this obviously.

---

### Post by fct on 2009-10-12
If you are manipulating arrays of char in C which hold strings, then you should use the functions in the string.h library with char pointers. Basically learn about these functions: malloc, realloc, free, strdup, strcpy (and strncpy), strcat (and strncat), sprintf, etc.

Be careful with the warnings in the manual pages about how they take care of NULL terminators. Strings in C are a whole different world compared with the String class in Java.

---

### Post by rbaleksandar on 2009-10-13
Thanks you very much. Will definitely follow your advice. :KS

---

### Post by Can+~ on 2009-10-13
> **fct said:**
> Be careful with the warnings in the manual pages about how they take care of NULL terminators. Strings in C are a whole different world compared with the String class in Java.

Try to avoid depending on NULL terminators and prefer the "strn..." family.

---

### Post by fct on 2009-10-14
> **Can+~ said:**
> Try to avoid depending on NULL terminators and prefer the "strn..." family.

The strn... functions limit the maximum amount of chars to work with, preventing segmentation faults and so on. But NULL terminators will still be considered and are the basis of C strings anyway. You can't get rid of that. :twisted:

---

