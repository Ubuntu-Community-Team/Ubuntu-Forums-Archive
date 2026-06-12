---
title: "Why can't I print the 1st charachter of an array?"
date: 2011-06-22
forum: Programming Talk
---

### Post by stamatiou on 2011-06-22
I want to print the first carachter of an array. The folowing code results in segmetation fault....
```
#include <stdio.h>

main()    {
char s[] = "george sss";
printf("%s",s[1]);
}
```
Also, in order to create a string, can I do it also like this:```
char string;
```?

---

### Post by cgroza on 2011-06-22
> **stamatiou said:**
> [/CODE]Also, in order to create a string, can I do it also like this:```
char string;
```?
Strings are nothing but arrays of characters, so here, you declare only 1 single char.

I think your segfault is there because you did not null terminated your string.
Add "/0" the end of it.
And you should declare main to return an int.

---

### Post by schauerlich on 2011-06-22
> **cgroza said:**
> Strings are nothing but arrays of characters, so here, you declare only 1 single char.

I think your segfault is there because you did not null terminated your string.
Add "/0" the end of it.
And you should declare main to return an int.

It's a string literal, so a null terminator is not the issue. (And by the way, it's \0, not /0).


> **stamatiou said:**
> I want to print the first carachter of an array. The folowing code results in segmetation fault....
```
#include <stdio.h>

main()    {
char s[] = "george sss";
printf("%s",s[1]);
}
```
Also, in order to create a string, can I do it also like this:```
char string;
```?

"%s" is for printing strings. A string is an array of characters. s[1] returns the second character in the array "s" (not the first - indexes start at 0, not 1). It segfaults because it's expecting a pointer to the first element of a char array, but you're just giving it a character. So, it boldly assumes you meant to do that, tries to dereference the memory address corresponding to the character value (in this case, 'e', whose value is 101). This is why you get a segfault.

To print a character, use "%c".

---

