---
title: "C, malloc, and segmentation faults"
date: 2009-07-14
forum: Programming Talk
---

### Post by JordyD on 2009-07-14
OK, so C isn't my strongest point.

But I've been *trying* to use it. 

This is what I've done:
```
int strapp(char* dest, char* src) {
	size_t destlen = strlen(dest);
	size_t srclen = strlen(src);
	char* newstring;

	if (destlen < destlen + srclen) {
		newstring = malloc(destlen + srclen);
		newstring[0] = '\0';
	}
	strcat(newstring, dest);
	strcat(newstring, src);
	free(dest);
	dest = newstring;
}
```

**EDIT:** In my local copy, I have an #include string.h, but I did not copy it to here, as slavik has pointed out. Just pretend it's really there.

This is supposed to append one string to another. So, for example, I could run this program
```
#include <stdio.h>
#include <stdlib.h>

int strapp(char* dest, char* src) {
	size_t destlen = strlen(dest);
	size_t srclen = strlen(src);
	char* newstring;

	if (destlen < destlen + srclen) {
		newstring = malloc(destlen + srclen);
		newstring[0] = '\0';
	}
	strcat(newstring, dest);
	strcat(newstring, src);
	free(dest);
	dest = newstring;
}

int main()
{
	char* messagepart = "Hello, ";
	char* messagepart2 = "world!";
	
	strapp(messagepart, messagepart2);
	
	printf("%s", messagepart);
	return 0;
}
```

And get the output:
```
Hello, world!
```

Unfortunately, I get this instead:
```
Segmentation fault
```
Not quite what I wanted.

I'm well aware of what that means. It means that I've been trying to use more memory than I'm allowed. Unfortunately, all looks well to me. Granted this is my first time trying to use malloc, so I'm probably not seeing something that's fairly obvious to somebody more experience. Anybody with said experience is welcome to post here. And I'd appreciate it if they did.

Thanks,
Jordy

---

### Post by slavik on 2009-07-14
so many errors ...

1. no string.h
2. why is strapp said to return a string but does not actually explicitly return anything
3. newstring may in some cases not be allocated any memory
4. when newstring is allocated, it doesn't have enough space (where is ending NULL stored?)
5. you are not actually changing the value of where dest points to
6. I am also pretty sure that you can't free dest and assign it a different value, because it would not be saved ... (please correct me if I am wrong).

---

### Post by Can+~ on 2009-07-14
7. char* messagepart = "Hello, "; are not allocating nothing actually, C++ can declare c-strings that way (but declaring a length). In C should be:
```
char messagepart[20] = {"Hello, "};
```

Funny that you're mimicking what strcat() does, and calling it inside the function.

---

### Post by JordyD on 2009-07-15
> **slavik said:**
> so many errors ...

1. no string.h
2. why is strapp said to return a string but does not actually explicitly return anything
3. newstring may in some cases not be allocated any memory
4. when newstring is allocated, it doesn't have enough space (where is ending NULL stored?)
5. you are not actually changing the value of where dest points to
6. I am also pretty sure that you can't free dest and assign it a different value, because it would not be saved ... (please correct me if I am wrong).

1. Sorry, I had included it in my files here, but left it out when I copied it onto the forum. I'll mention that in the OP so other readers are not thrown off.
2. It actually returns an int, but it doesn't return anything, which is a mistake on my part. I've changed it to void in my local copy.
3. Err, why?
4. That makes sense. I've changed it to allocate +1.
5. Also makes sense. I've changed it to "dest = &newstring", is that correct?
6. How would I then ensure that there is no memory leak when I change what dest points to? "free((char*)(dest + 1));" ?

Thank you for your response.

---

### Post by JordyD on 2009-07-15
> **Can+~ said:**
> 7. char* messagepart = "Hello, "; are not allocating nothing actually, C++ can declare c-strings that way (but declaring a length). In C should be:
```
char messagepart[20] = {"Hello, "};
```

Funny that you're mimicking what strcat() does, and calling it inside the function.

7. That would be me having more experience with C++ than C, and often getting them confused. I so wish that C++ was a pure superset of C.

I was under the impression that strcat left it to the caller to allocate space.

Again, thanks.

I'm going to bed now, I'll read in the morning.

---

### Post by Can+~ on 2009-07-15
Ok, an explanation on what's happening.

First of, you declare a first variable, named "msg" and it will contain "Hello, " plus some space to add stuff on it:

```
[H|e|l|l|o|,| |0| | | | | | | | | ]
```

What strcat() (the one you're calling) will do, is fill the rest with the second argument, in this example, "World!"

```
[H|e|l|l|o|,| |W|o|r|l|d|0| | | | ]
```
(Notice how the 0 has been displaced, it marks the end of the string)

So you don't actually need to malloc()/free() anything, strcat will copy the content, not a reference.

A simple way to implement your function (plus an extra), is with memcpy and some pointer arithmetic

[PHP]void strapp(char *base, const char* appended, const unsigned int overlap)
{
	memcpy(base+strlen(base)-overlap, appended, strlen(appended));
}[/PHP]

Plus, I added the variable overlap, so:
overlap 0: "Hello, World!"
overlap 1: "Hello,World!"
overlap 2: "HelloWorld!"

Full running example

[PHP]#include <stdio.h>
#include <string.h>
#include <stdlib.h>

void strapp(char *base, const char* appended, const unsigned int overlap)
{
	memcpy(base+strlen(base)-overlap, appended, strlen(appended));
}

int main(int argc, char **argv)
{
	char msg[30] = {"Hello, "};
	
	strapp(msg, "World!", 0);
	
	printf("%s\n", msg);

	return 0;
}
[/PHP]

---

### Post by JordyD on 2009-07-15
> **Can+~ said:**
> Ok, an explanation on what's happening.

First of, you declare a first variable, named "msg" and it will contain "Hello, " plus some space to add stuff on it:

```
[H|e|l|l|o|,| |0| | | | | | | | | ]
```

What strcat() (the one you're calling) will do, is fill the rest with the second argument, in this example, "World!"

```
[H|e|l|l|o|,| |W|o|r|l|d|0| | | | ]
```
(Notices how the 0 has been displaced, it marks the end of the string)

So you don't actually need to malloc()/free() anything, strcat will copy the content, not a reference.

Well, yes, but what if this happens:
```
[H|e|l|l|o|,| |0| | ]
```

Then when I call strcat:
```
[H|e|l|l|o|,| |w|o|r]
```
And then a segmentation fault.

With strapp, I was trying to make it so I could handle an undefined number of letters.

**EDIT:** God, you're fast at editing your posts.
OK, *now* I'm going to bed. I'll read the other half of your post in the morning.

---

### Post by Can+~ on 2009-07-15
> **JordyD said:**
> Well, yes, but what if this happens:
```
[H|e|l|l|o|,| |0| | ]
```

Then when I call strcat:
```
[H|e|l|l|o|,| |w|o|r]
```
And then a segmentation fault.

With strapp, I was trying to make it so I could handle an undefined number of letters.

You can't redefine the length of a variable that has been stacked (basically, where it could grow?). 

One way you could do it is having the "base" being allocated on the heap and then reallocing() it (which is expensive); or inventing a linked-list which handles strings, or... well, many other ways to solve it.

---

### Post by nvteighen on 2009-07-15
Another issue in your original strapp function is the following.

1) You call it using main's **messagepart** as argument for strapp's **dest**. What that means is that the memory address held by **dest** will be the same that is held by **messagepart**.

2) In strapp, you then dynamically allocate a (char *) called **newstring**. This is a pointer holding some memory address.

3) You then do **dest = newstring**. So, the memory address originally held by **dest** (which was the same held by **messagepart**) is now replaced by the one held by **newstring**.

4) The function returns. All stack variables die, including **dest**

So, the **messagepart** pointer in main remains untouched. Why? Because you were manipulating **dest** and that pointer died afterwards.

When you want a function to modify a pointer that's been declared in another scope, you use a double pointer. In other words, you use a pointer that holds the memory address of the pointer you want to modify... And you modify it by dereferencing the double pointer once with * so you get the original pointer... )doing it twice with ** will get the original pointer's data). If **dest** would have been declared as a (char **), then ***dest = newstring** would have effectively modified the **messagepart** pointer at main.

---

### Post by JordyD on 2009-07-15
> **Can+~ said:**
> You can't redefine the length of a variable that has been stacked (basically, where it could grow?). 

One way you could do it is having the "base" being allocated on the heap and then reallocing() it (which is expensive); or inventing a linked-list which handles strings, or... well, many other ways to solve it.

Well, I thought, why not make a new char array with the contents you want, then free the old one and change what your pointer points to.

It has to be doable. How else would other languages let you just mystring = mystring + yourstring without being expensive?

> **nvteighen said:**
> Another issue in your original strapp function is the following.

1) You call it using main's **messagepart** as argument for strapp's **dest**. What that means is that the memory address held by **dest** will be the same that is held by **messagepart**.

2) In strapp, you then dynamically allocate a (char *) called **newstring**. This is a pointer holding some memory address.

3) You then do **dest = newstring**. So, the memory address originally held by **dest** (which was the same held by **messagepart**) is now replaced by the one held by **newstring**.

4) The function returns. All stack variables die, including **dest**

So, the **messagepart** pointer in main remains untouched. Why? Because you were manipulating **dest** and that pointer died afterwards.

When you want a function to modify a pointer that's been declared in another scope, you use a double pointer. In other words, you use a pointer that holds the memory address of the pointer you want to modify... And you modify it by dereferencing the double pointer once with * so you get the original pointer... )doing it twice with ** will get the original pointer's data). If **dest** would have been declared as a (char **), then ***dest = newstring** would have effectively modified the **messagepart** pointer at main.

But when you're manipulating pointers, you're manipulating by reference, so why would dest die? I've done plenty of small functions that manipulated char arrays without having to return anything.

For example:
```
void copy(char to[], char from[])
{
        int i;

        i = 0;
        while ((to[i] = from[i]) != '\0')
                ++i;
}
```

This compiles as far as I'm aware, and it does what I want. (I know this is in the standard library as strcpy, but I got this from the K&R book)

Thank you for your help so far.

---

### Post by JordyD on 2009-07-15
Bump.

I'd really like to hear some explanation.

---

### Post by nvteighen on 2009-07-16
> **JordyD said:**
> 
But when you're manipulating pointers, you're manipulating by reference, so why would dest die? I've done plenty of small functions that manipulated char arrays without having to return anything.

**dest** will die because it's declared on that function's call stack. Its reference won't die, but the variable will, like any other stack variabnle.

> 
For example:
```
void copy(char to[], char from[])
{
        int i;

        i = 0;
        while ((to[i] = from[i]) != '\0')
                ++i;
}
```

This compiles as far as I'm aware, and it does what I want. (I know this is in the standard library as strcpy, but I got this from the K&R book)


That works because you're not changing the memory region where **to** is pointing to... You're changing ***(to + i)**, not **to**. In your earlier code, you malloc()'ed a new place in memory and the replaced a pointer's reference by that one.

---

### Post by PmDematagoda on 2009-07-16
This code seems to work:-
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void strapp(char **str1, char **str2) {
	size_t destlen = strlen(*str1);
	size_t srclen = strlen(*str2);
	char *newstring;

	if (destlen < destlen + srclen) {
	  newstring = (char *) malloc( (destlen + srclen + 1) * sizeof(char) );
		newstring[0] = '\0';
	}
	strcat(newstring, *str1);
	strcat(newstring, *str2);

	*str1 = newstring;
}

int main()
{
	char *messagepart = "Hello, ";
	char *messagepart2 = "world!";
	
	strapp(&messagepart, &messagepart2);
	
	printf("%s", messagepart);
	return 0;
}
```
basically the biggest change done was to pass a pointer to a pointer, this allows you to manipulate the messagepart and messagepart2 pointers directly in the strapp function, exactly like what you would do in a call by reference. Also, you probably can't free the memory pointed to by the messagepart pointers since they memory was statically allocated at run time. Also the type of the strapp pointer was changed to void, since you aren't returning anything in the first place, although you could return a char * pointer to the new string to make things easier.

---

### Post by JordyD on 2009-07-16
> **nvteighen said:**
> **dest** will die because it's declared on that function's call stack. Its reference won't die, but the variable will, like any other stack variabnle.



That works because you're not changing the memory region where **to** is pointing to... You're changing ***(to + i)**, not **to**. In your earlier code, you malloc()'ed a new place in memory and the replaced a pointer's reference by that one.

Thank you. This makes sense now.

> **PmDematagoda said:**
> This code seems to work:-
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void strapp(char **str1, char **str2) {
	size_t destlen = strlen(*str1);
	size_t srclen = strlen(*str2);
	char *newstring;

	if (destlen < destlen + srclen) {
	  newstring = (char *) malloc( (destlen + srclen + 1) * sizeof(char) );
		newstring[0] = '\0';
	}
	strcat(newstring, *str1);
	strcat(newstring, *str2);

	*str1 = newstring;
}

int main()
{
	char *messagepart = "Hello, ";
	char *messagepart2 = "world!";
	
	strapp(&messagepart, &messagepart2);
	
	printf("%s", messagepart);
	return 0;
}
```
basically the biggest change done was to pass a pointer to a pointer, this allows you to manipulate the messagepart and messagepart2 pointers directly in the strapp function, exactly like what you would do in a call by reference. Also, you probably can't free the memory pointed to by the messagepart pointers since they memory was statically allocated at run time. Also the type of the strapp pointer was changed to void, since you aren't returning anything in the first place, although you could return a char * pointer to the new string to make things easier.

I was beginning to do something along these lines. But I do have two questions: Why do you cast malloc's return value as char*, and why do you multiply (destlen+srclen+1) by sizeof(char)? I thought that declaring them as size_t made that unnecessary.

Again, thanks everyone so far. I've been learning a lot from this thread.

**EDIT:** Is freeing dest out of the question?

---

### Post by smartbei on 2009-07-16
malloc returns a void *, so as a Best Practice there should be a cast to the type of pointer you want. It is not necessary however, since casting from void * to any type of pointer is automatic.

As for multiplying by sizeof(char) - there could theoretically be a system where a char is not one byte, and if that is the case then you want to allocate so many chars, not so many bytes. This is not the case in any modern system, but you never know - perhaps things will change.

---

### Post by JordyD on 2009-07-16
> **smartbei said:**
> malloc returns a void *, so as a Best Practice there should be a cast to the type of pointer you want. It is not necessary however, since casting from void * to any type of pointer is automatic.

As for multiplying by sizeof(char) - there could theoretically be a system where a char is not one byte, and if that is the case then you want to allocate so many chars, not so many bytes. This is not the case in any modern system, but you never know - perhaps things will change.

So casting char* is good style and sizeof(char) is for compatibility. Thank you. I hope I remember this when I do it myself. :D

---

### Post by johnl on 2009-07-16
Hi,

Actually the C standard states that sizeof(char) == 1.  so multiplying by sizeof(char) is unnecessary. 

The number of bits per character is allowed to be any number greater than or equal to 8 however :)

---

### Post by nvteighen on 2009-07-16
> **JordyD said:**
> 
**EDIT:** Is freeing dest out of the question?

Of course, doing that you'll erase the original string... which in your case is a stack variable, thus dooming the program to crash.

---

### Post by JordyD on 2009-07-16
> **nvteighen said:**
> Of course, doing that you'll erase the original string... which in your case is a stack variable, thus dooming the program to crash.

Rawr. So best not to use this method.

---

### Post by smartbei on 2009-07-16
> **johnl said:**
> 
Actually the C standard states that sizeof(char) == 1.  so multiplying by sizeof(char) is unnecessary.


A bit of research proves you right - thanks for the correction!

---

### Post by PmDematagoda on 2009-07-16
> **johnl said:**
> Hi,

Actually the C standard states that sizeof(char) == 1.  so multiplying by sizeof(char) is unnecessary. 

The number of bits per character is allowed to be any number greater than or equal to 8 however :)

Well, no one got killed for trying to make an effort to be as thorough as possible.:)

---

