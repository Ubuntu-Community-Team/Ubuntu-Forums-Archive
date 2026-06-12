---
title: "boundary in character array"
date: 2013-02-01
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-01
Hi,
I have a question regarding the boundary in character array.

Scenario:
1. I initialized a character array char str[10] with 'b' using memset;
2. Then I filled characters from str[0] to str[4] with 'a'
3. So I was expecting to get a's from str[0-4] and b's from str[5-9].(*str[a-b] convention just for explaining scenario*) All that is fine and I am getting the expected output.

But **my question is, after str[9] what happens ?**. I know that strings/(character arrays also right ? they are the same) are NULL terminated. So when I print out the ascii at str[10], I was hoping to find 0(ascii of NULL). But that's not what I'm getting.

Please find the code below.

```

#include <stdio.h>

int main(void)
{
 char str[10];
 int i = 0;

 memset(str,98,10);

 for(i=0;i<5;i++)
  str[i] = 'a';

 for(i=0;i<100;i++)
  printf("\nstr[%d] == [%d]",i,str[i]);

 return 0;
}

```

Output :
```

str[0] == [97]
str[1] == [97]
str[2] == [97]
str[3] == [97]
str[4] == [97]
str[5] == [98]
str[6] == [98]
str[7] == [98]
str[8] == [98]
str[9] == [98]
**str[10] == [64]**
str[11] == [0]
str[12] == [0]
str[13] == [0]
str[14] == [0]
str[15] == [0]
str[16] == [16]
str[17] == [22]
str[18] == [-27]
str[19] == [85]
```

On seeing the output, I'm **starting to feel that, in memory, there is no NULL, adding a NULL is the duty of the format specifier(%s) that is used only for printing purpose(but not in memory).**
Please advise.
Thanks

---

### Post by trent.josephsen on 2013-02-01
str[9] is the 10th element of str. str[10] is outside the bounds of the array.

C does not enforce null termination of strings. If you want your strings to be null terminated, you must initialize them appropriately and only use functions that respect null termination. strcat, for example, uses the null terminators of both strings to determine how many characters from the second argument to append to the first, and it adds the null terminator at the end.

memset is a function that operates on memory, not null-terminated strings. You took an uninitialized array, filled it with 98s using memset, then changed the first few elements to 97s instead. Nowhere along the line was it ever null terminated.

If you printed it with printf("%s", str), you'd find that printf would continue printing characters until it reached a 0 or caused a segmentation fault. This is because %s operates on C strings -- it only knows when to stop because it finds the terminating zero. (The null byte, btw, isn't part of the output -- it's just part of the internal representation of a C string.)

---

### Post by Vaphell on 2013-02-01
if you had your string initialized you'd overwrite the null char. If you manage strings by hand you have to leave the SIZE-1 element alone.
 

```
#include <stdio.h>

int main(void)
{
  char str[] = "abcdefghi"; **// 9 chars**
  int i = 0;

  puts( "BEFORE" );
  printf( "str: %s\n", str );
  printf( "sizeof(str): %lu\n", sizeof(str)/sizeof(str[0]) );
  for( i=0; i<sizeof(str)/sizeof(str[0]); i++ )
    printf( "str[%d]: '%c' (%d)\n", i, str[i], str[i] );

  memset(str, 'X', 10 );
  puts( "AFTER" );
  printf( "str: %s\n", str );
  printf( "sizeof(str): %lu\n", sizeof(str)/sizeof(str[0]) );
  for( i=0; i<sizeof(str)/sizeof(str[0]); i++ )
    printf( "str[%d]: '%c' (%d)\n", i, str[i], str[i] );
  return 0;
}
```

```
$ ./arr 
BEFORE
str: abcdefghi
**sizeof(str): 10**
str[0]: 'a' (97)
str[1]: 'b' (98)
str[2]: 'c' (99)
str[3]: 'd' (100)
str[4]: 'e' (101)
str[5]: 'f' (102)
str[6]: 'g' (103)
str[7]: 'h' (104)
str[8]: 'i' (105)
**str[9]: '' (0)**
AFTER
str: XXXXXXXXXX@
sizeof(str): 10
str[0]: 'X' (88)
str[1]: 'X' (88)
str[2]: 'X' (88)
str[3]: 'X' (88)
str[4]: 'X' (88)
str[5]: 'X' (88)
str[6]: 'X' (88)
str[7]: 'X' (88)
str[8]: 'X' (88)
**str[9]: 'X' (88)**

```

---

### Post by IAMTubby on 2013-02-01
> **trent.josephsen said:**
> 
If you printed it with printf("%s", str), you'd find that printf would continue printing characters until it reached a 0 or caused a segmentation fault.

> **Vaphell said:**
> if you had your string initialized you'd overwrite the null char. If you manage strings by hand you have to leave the SIZE-1 element alone.


thanks trent.josephsen, Vaphell for your replies :). 

May I slightly rephrase the question,
Suppose I have a string char str[10], then I would want to put values at a maximum till str[9]. And then, say I print using printf("\nstr == [%s]",str);, **my question is, who takes care of putting a '\0' at the end of the 9 chars, the developer or glibc ?**
What I'm suggesting is, C can very easily go and put a str[10]=0;(NULL at the end) when it sees that char str[10] is declared so that printf("%s",str) will print a worst-case of 10 characters any time. But it doesn't do it and keeps searching/printing until it finds a NULL  Why ?

---

### Post by Tony Flury on 2013-02-02
> **IAMTubby said:**
> thanks trent.josephsen, Vaphell for your replies :). 

May I slightly rephrase the question,
Suppose I have a string char str[10], then I would want to put values at a maximum till str[9]. 

If you have an str[10] array it goes from str[0] to str[9] which includes any terminator that your code requires.
> 
And then, say I print using printf("\nstr == [%s]",str);, **my question is, who takes care of putting a '\0' at the end of the 9 chars, the developer or glibc ?**

The developer is responsible for storing or preserving the null terminator. If you don't and your code is sufficiently complex then when your print your strings you will get garbage after your text,,
> 
What I'm suggesting is, C can very easily go and put a str[10]=0;(NULL at the end) when it sees that char str[10] is declared so that printf("%s",str) will print a worst-case of 10 characters any time. But it doesn't do it and keeps searching/printing until it finds a NULL  Why ?
When you declare an array in C the compiler does not retain any Information  about the size of memory areas allocated (by declaration or malloc) and does not do any bounds checking at run time, the programmer has to do that work., because that is the way that C is defined. That lack of bounds checking puts more work in the hands of the developer but means that in general a C program can be very efficient (as you don't get lots of compiler generated code to check array boundaries etc)
The other benefit of a specific terminator is that you can declare an array of say 100 characters, but then easily store 7 say, and so long as it is terminated correctly that is all you need to do.

---

### Post by Bachstelze on 2013-02-02
> **IAMTubby said:**
>  I know that strings/(character arrays also right ? they are the same) are NULL terminated.

No, strings and character arrays are not the same thing. A string is something that you store in a character array, but a character array can contain a lot of other things. If a character array does not contain a string, it will not be null terminated. And in your example, your character array does not contain a string.

> **IAMTubby said:**
> 
What I'm suggesting is, C can very easily go and put a str[10]=0;(NULL at the end) when it sees that char str[10] is declared so that printf("%s",str) will print a worst-case of 10 characters any time. But it doesn't do it and keeps searching/printing until it finds a NULL  Why ?

Because that wouldn't be in the spirit of C. In particular, it would hurt efficiency in both time (every array allocation would require one additional memory access) and space (one additional byte). And of course even if it did that you could very well overwrite the "extra" byte, so it would be of questionable usefulness.

> **Tony Flury said:**
> When you declare an array in C the compiler does not retain any Information  about the size of memory areas allocated

This is not entirely true. You can do something like

```
char s[10];
int n = sizeof(s);
```

and n will be 10. Everything else you said is true, of course.

---

### Post by IAMTubby on 2013-02-02
> **Tony Flury said:**
> 
The developer is responsible for storing or preserving the null terminator.
That lack of bounds *edited by me*means that a C program can be very efficient (as you don't get lots of compiler generated code to check array boundaries etc)


> **Bachstelze said:**
> 
Because that wouldn't be in the spirit of C. In particular, it would hurt efficiency in both time (every array allocation would require one additional memory access) and space (one additional byte).

Thanks a lot Tony Flury,Bachstelze for your wonderful explanation. I completely understand.

> **trent.josephsen said:**
> 
If you printed it with printf("%s", str), you'd find that printf would continue printing characters until it reached a 0 or caused a segmentation fault.

> **Vaphell said:**
> if you had your string initialized you'd overwrite the null char. If you manage strings by hand you have to leave the SIZE-1 element alone.

Thanks Vaphell, trent.josephsen for starting it off and making me think.

---

### Post by Bachstelze on 2013-02-02
See my first paragraph above, I added it after the fact so you might not have seen it, and it's really the most important part.

---

