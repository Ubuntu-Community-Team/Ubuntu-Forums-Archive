---
title: "[SOLVED] Caesar cipher in C"
date: 2008-03-23
forum: Programming Talk
---

### Post by nvteighen on 2008-03-23
Hi there!
I've been experimenting these days with some C just because of fun and need some help.

This code tries to substitute one single letter into a number (A=0, B=1, C=2, etc.), but for some reason it doesn't work and gets stuck into an infinite loop. This is the first step for a little Caesar Cipher encoder, where letters are "summed" by a key. So, I need to convert letters into numbers first. (I don't want any help on the rest)

```

#include <stdio.h>
#include <string.h> //for strlen();
#include <ctype.h> //for toupper();

char *abc = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"; //Alphabet defined as global variable

int subst(char x); //Function defined

int main(void)
{
	char key;
	int key2;

	puts("Enter a 1 character long text");
	scanf("%c", &key);
	
	key = toupper(key); //converts all letters to uppercase
	key2 = subst(key); //calling substitution function
	
	printf("%d\n", key2);
	
	return 0;
}

int subst(char x)
{
	int out, i, len;	
	len = strlen(abc); //do len be abc string's length
	
	for((i = 0); (i = len); i++)
	{
		if(abc[i] == x)
		{
			out = i;
		}
	/*This should search each abc's characters and compare it with x (which is the key variable) and, if they're the same, the function will return the corresponding character's place in the array as result (so, A = 0, B = 1, etc.)*/
	}
	
	return out;
}

```

Thanks!

---

### Post by mike_g on 2008-03-23
> for((i = 0); (i = len); i++)
Here you set i to len each loop. You want:
```
for((i = 0); (i < len); i++)
```
;)

---

### Post by ruy_lopez on 2008-03-23
The "for" loop looks weird, try this:

```

for (i = 0; i < len; i++)

```

or using pointer arithmetic:

```

/* include <string.h> */
int subst(char x)
{
       char *p;

       p = index(abc, x);
       return (p - abc);
}

```

---

### Post by nvteighen on 2008-03-23
Thank you very much! Compiled and substitution works perfectly. Now I'll try to make it ignore numbers (if I enter "2", I get "0", which is an "a").

But, just curious, why shouldn't I use (i <= len) instead?

---

### Post by ruy_lopez on 2008-03-23
> **nvteighen said:**
> 
But, just curious, why shouldn't I use (i <= len) instead?

array indexes start at 0. So when you test using "< len", it stops at len - 1, which is correct for an array.

In other words, the length of str = "string" is 6 chars, but the last char is at str[5].

---

### Post by Can+~ on 2008-03-23
Tip: You know that you can get the ascii code of any character by using 'something'. So use that, and for each character on a string, substracting the first letter:
[PHP]
char string[20] = "abcdef"

//blah blah loop
numb = string[i] - 'a'[/PHP]

it would produce something like:
'a' - 'a' = 0
'b' - 'a' = 1
'c' - 'a' = 2
...

And you can filter that the input is not < 'a' and > 'z'

---

### Post by nvteighen on 2008-03-23
> **Can+~ said:**
> Tip: You know that you can get the ascii code of any character by using 'something'. So use that, and for each character on a string, substracting the first letter:
[PHP]
char string[20] = "abcdef"

//blah blah loop
numb = string[i] - 'a'[/PHP]

it would produce something like:
'a' - 'a' = 0
'b' - 'a' = 1
'c' - 'a' = 2
...

And you can filter that the input is not < 'a' and > 'z'
Well, that's easier and avoids using that global array. And also avoids the using ctype's isalpha()! Thanks!

---

### Post by nvteighen on 2008-03-23
OK, the program works great! Thank you all for your advices!

---

