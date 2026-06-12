---
title: "Howto declare a string without knowing how&#65279; big it would be in c?"
date: 2010-04-25
forum: Programming Talk
---

### Post by Face_Man on 2010-04-25
Hello All, 

if i want to declare a string but i don't know how&#65279; big it would be, it could be 300 or 7000 or maybe more.

for example:
```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
char *FristFun(char *Parm){
	char  ReturnStr=malloc(1*sizeof(char));
	//Do somthing unique in this function
	ReturnStr = realloc(ReturnStr,(strlen(ReturnStr) + strlen(Parm)+1));

	strcpy(ReturnStr , Parm);
	return ReturnStr;
}

char *SecondFun(char *Parm){
	char ReturnStr = malloc(1*sizeof(char));
	//Do somthing unique in this function
	ReturnStr = realloc(ReturnStr,(strlen(ReturnStr) + strlen(Parm)+1));
	strcpy(ReturnStr , Parm);
	return ReturnStr;
}

char *ThirdFun(char *Parm){
	char ReturnStr = malloc(1*sizeof(char));
	//Do somthing unique in this function
	ReturnStr = realloc(ReturnStr,(strlen(ReturnStr) + strlen(Parm)+1));
	strcpy(ReturnStr , Parm);
	return ReturnStr;
}
int main() {

	char FristReturn = malloc(1*sizeof(char));
	char SecondReturn = malloc(1*sizeof(char));
	char ThirdReturn = malloc(1*sizeof(char));
   
    	{//Get Values
		strcpy(FristReturn,FristFun("111111111111111111111111"));
		strcpy(SecondReturn,SecondFun("2222222222222222222222"));
		strcpy(ThirdReturn,ThirdFun("3333333333333333333"));
	}

	printf("\n============================================\n");
	printf("FristReturn:\n\t%s\n",FristReturn);
	printf("SecondReturn:\n\t%s\n", SecondReturn);
	printf("ThirdReturn:\n\t%s\n", ThirdReturn);
 	printf("\n============================================\n\n");
    	{//Free Var's
		free(FristReturn);
		 free(SecondReturn);
		 free(ThirdReturn);
	}
	return 0;
}

```

this is just an example the function should return a bigger string than this. however the programing dose not seem to be working and from what i understand i have to use malloc and realloc to change the size of char.


Therefore, how can i declare a dynamic char that could be as big as what i store in it ? 

Any help would be much appreciated.

---

### Post by slavik on 2010-04-25
no you can't.

---

### Post by phrostbyte on 2010-04-25
You have to keep track of the capacity of the array, and then realloc if the actual size of string gets to the capacity of the array. AFIAK, realloc is not always guaranteed to succeed. What you have to in the case realloc fails is memcpy the entire array to a new, larger array, and then free the old array (although I think realloc will do this for you). Essentially this is what the string (and vector) implementation in C++ does. So you can do it, but it is a very expensive operation to resize a large string, and should be avoided if possible.

---

### Post by LKjell on 2010-04-26
hmm do this?

```
char* str = "Hello\0";
```

---

### Post by Bachstelze on 2010-04-26
> **LKjell said:**
> hmm do this?

```
char* str = "Hello";
```

No, the point is that you don't know in advance how large the string will be. Obviously that means you also don't know what it is.

---

### Post by LKjell on 2010-04-26
> **Bachstelze said:**
> No, the point is that you don't know in advance how large the string will be. Obviously that means you also don't know what it is.

oh trust me you always know. If there is input then a modified fgets and getline will do its job. There is also dynamic allocation during runtime.

---

### Post by Compyx on 2010-04-26
If you just want to grab a copy of a string then you can do something like this:
```

char *dupstr(const char *s)
{
    size_t n = strlen(s) + 1;
    char *p = malloc(n);
    if (p != NULL) memcpy(p, s, n);
    return p;
}

```

Many C implementations provide a function strdup() as an extension, which does what the above function does. strdup() is not part of the standard C library so you would loose a little portability by using it.

As a side note: sizeof(char) is 1 by definition, so in stead of writing:
```

x = malloc(n * sizeof(char));

```
you can simply write:
```

x = malloc(n);

```

HTH

---

### Post by Bachstelze on 2010-04-26
> **Compyx said:**
> 
As a side note: sizeof(char) is 1 by definition, so in stead of writing:
```

x = malloc(n * sizeof(char));

```
you can simply write:
```

x = malloc(n);

```

However what it one wants to switch from plan chars to, say, Unicode characters? A simple

```
sed 's/sizeof(char)/sizeof(your_unicode_char_here)/g'
```

would do. If you just assumed it to be 1, you're screwed.

---

### Post by phrostbyte on 2010-04-26
> **Compyx said:**
> If you just want to grab a copy of a string then you can do something like this:
```

char *dupstr(const char *s)
{
    size_t n = strlen(s) + 1;
    char *p = malloc(n);
    if (p != NULL) memcpy(p, s, n);
    return p;
}

```

Many C implementations provide a function strdup() as an extension, which does what the above function does. strdup() is not part of the standard C library so you would loose a little portability by using it.

As a side note: sizeof(char) is 1 by definition, so in stead of writing:
```

x = malloc(n * sizeof(char));

```
you can simply write:
```

x = malloc(n);

```

HTH

That's a very nice example. :) Here is just a possible modification.

This function _should_ (cross-fingers), resize a string, without modifying its contents. It does so by allocating a new chunk of memory, copying it over, freeing the original chuck, and rebasing the pointer. It *assumes* s points to some data allocated on the heap, and that n is NOT less then the data allocated. And yes if there are any other pointers to this string, they are invalid after calling this. Might be a way to avoid these disadvantages (double pointers, heh)..

```

char *strresize(char* const s, size_t n)
{
    char *p = malloc(++n);
    if (p != NULL) memcpy(p, s, n);
    else return;
    free(s);
    return p;
}

```

Now someone else can code a strcat that calls this function as needed. :) Wow, a mildly safe strcat in C. :P

---

### Post by LKjell on 2010-04-26
modify const is kinda risky... And if you allocate the string on the stack free will give you a nice Christmas tree.

---

### Post by Compyx on 2010-04-26
> **Bachstelze said:**
> However what it one wants to switch from plan chars to, say, Unicode characters? A simple

```
sed 's/sizeof(char)/sizeof(your_unicode_char_here)/g'
```

would do. If you just assumed it to be 1, you're screwed.

No need to use sed:
```

some_type *t = malloc(n * sizeof *t);

```

This way you always get the correct size.

---

### Post by phrostbyte on 2010-04-26
> **LKjell said:**
> modify const is kinda risky... And if you allocate the string on the stack free will give you a nice Christmas tree.

Unfortunately I don't think there is any [simple] way to detect if a pointer is pointing to a stack object, or a heap object, or really, anything useful at all. If there is, someone enlighten me!

There always seems to be 65 different ways to kill yourself using C. :)

---

### Post by LKjell on 2010-04-26
> **phrostbyte said:**
> Unfortunately I don't think there is any [simple] way to detect if a pointer is pointing to a stack object, or a heap object, or really, anything useful at all. If there is, someone enlighten me!

There always seems to be 65 different ways to kill yourself using C. :)

Well we do know the string we put into the function. But the const keyword you need to change. Cannot free something that is locked. Beside a function should do only one thing. One reason why strdup was left out since it does two things at the same time. And it was hard to decide if it should be in stdlib.h or in string.h when they reviewed it. Though I find it is one of the most useful function when you are dealing with string copying.

---

### Post by phrostbyte on 2010-04-26
> **LKjell said:**
> Well we do know the string we put into the function. But the const keyword you need to change. Cannot free something that is locked. Beside a function should do only one thing. One reason why strdup was left out since it does two things at the same time. And it was hard to decide if it should be in stdlib.h or in string.h when they reviewed it. Though I find it is one of the most useful function when you are dealing with string copying.

You are definitely right about the const.

But the function is doing 'one' thing: resizing the string. I suppose you could move the free out of the function, but if the user forgets to do it themselves they would have a nice memory leak. I don't know if you can win either way. I like to make functions that don't "logically" create object (eg: foo_create), handle memory management themselves, if necessary. Ideally the library user never uses free() or malloc(), ever. :) eg: foo_create, foo_free instead

---

### Post by LKjell on 2010-04-26
> **phrostbyte said:**
> You are definitely right about the const.

But the function is doing 'one' thing: resizing the string. :) I suppose you could move the free out of the function, but if the user forgets to do it themselves they would have a nice memory leak. I don't know if you can win either way. I like to make functions that don't "logically" create object (eg: foo_create), handle memory management themselves, if necessary.

If you cannot handle memory management then C would not be a good language to write in. Beside to resize a string we do have realloc. The reason why we want to copy a string is to modify one while keep the other as a copy. Like doing strtok on one of them.

And if the string is allocated on the stack you can either use it or leave it. That kind of memory is already "lost" and cannot be resized.

---

### Post by gil_johnson on 2010-04-28
> **Face_Man said:**
> Hello All, 

if i want to declare a string but i don't know how&#65279; big it would be, it could be 300 or 7000 or maybe more.

for example:
```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
char *FristFun(char *Parm){
    char  ReturnStr=malloc(1*sizeof(char));
    //Do somthing unique in this function
    ReturnStr = realloc(ReturnStr,(strlen(ReturnStr) + strlen(Parm)+1));
    [...]

```this is just an example the function should return a bigger string than this. however the programing dose not seem to be working and from what i understand i have to use malloc and realloc to change the size of char.


Therefore, how can i declare a dynamic char that could be as big as what i store in it ? 

Any help would be much appreciated.

I think you might be looking for the "struct hack" in C89, which was formalized as the "flexible array member" in C99. The last member of a structure can be an array of 1 character in C89, or an array of zero length in C99. When you know the length, you have to allocate enough room for the stuct + string, and just write over the space, even though C89 thinks you are writing past the end of the array. 
For an example look at:
[http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/Zero-Length.html](http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/Zero-Length.html)
Gil

---

