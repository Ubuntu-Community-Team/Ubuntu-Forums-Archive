---
title: "NULL, bad programming practice?"
date: 2013-02-14
forum: Programming Talk
---

### Post by IAMTubby on 2013-02-14
Hello,
Say I have an array char str[10], which I have memset to 0. and then filled all characters from str[0] to str[9]. I then print it out using printf("%s",str);. It gets printed alright, but am I just getting lucky here ? For it to print correctly, str[10] has to be NULL, correct ? something which I have not done. 

Here's the code and the array I printed for more locations than the length of the array. str[10] seems to be NULL, but that's something I have not done.

```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
 char str[10];
 int i = 0;

 memset(str,0,10);

 for(i=0;i<10;i++)
  str[i] = 'a' + i;

 for(i=0;i<100;i++)
  printf("\n*(str + %d) == %d",i,*(str + i));
 
 return 0;
}
```

_Printing locations starting from start location of array_
```

*(str + 0) == 97
*(str + 1) == 98
*(str + 2) == 99
*(str + 3) == 100
*(str + 4) == 101
*(str + 5) == 102
*(str + 6) == 103
*(str + 7) == 104
*(str + 8) == 105
*(str + 9) == 106
***(str + 10) == 0**
*(str + 11) == 0
*(str + 12) == 10
*(str + 13) == -1
*(str + 14) == -16
..
..
```

Thanks.

---

### Post by Some Penguin on 2013-02-15
Yes, avoid.

---

### Post by jwbrase on 2013-02-15
> **IAMTubby said:**
> Hello,
Say I have an array char str[10], which I have memset to 0. and then filled all characters from str[0] to str[9]. I then print it out using printf("%s",str);. It gets printed alright, but am I just getting lucky here ? For it to print correctly, str[10] has to be NULL, correct ? something which I have not done. 


Yes, although "NULL" in C refers to the null pointer value (which is zero on most systems, hence the name). '\0' is the ASCII/Unicode null character.

---

### Post by ofnuts on 2013-02-15
You have to make sure that your string is null terminated, so doing it explicitly after copying data ill make it more obvious to anyone reading you code (and this includes you, some days later).

But the most questionable thing in your code is using "\n" at the beginning of the format strings.... (am I starting a religious war here?). One reason is that when the output is a "tty", things get flushed/displayed by the C runtime only when it sees a "\n". So with code like this:

```

printf("\nline1");
// some code runs here
printf("\nline2");
// some code breaks here
printf("\nline3");

```
You will only see "line1" on your terminal and thus you will search a problem between  "line1" and "line2" while the problem is really between "line2" and "line3".

---

### Post by r-senior on 2013-02-15
> **IAMTubby said:**
> Say I have an array char str[10] ... str[10] has to be NULL, correct ?
If you have an array of 10 char, str[10] is the eleventh char and is beyond the space allocated for the string. The ten characters of the string are indexed 0 to 9.

So, yes, you do need to make sure the last character of the string is the null character '\0', but that would be str[9] rather than str[10].

---

### Post by spjackson on 2013-02-15
+1 to what ofnuts said. Putting \n at the beginning of a string is bad programming practice. Ignoring compiler warnings about memset is bad programming practice.

Accessing an array outside its bounds is not merely bad programming practice; it is [undefined behaviour]("http://en.wikipedia.org/wiki/Undefined_behavior") and therefore dangerous. This is equally the case whether you do it explicitly in your second for loop, or you do it implicitly by passing an array of characters that you have not null-terminated to a function that requires a null-terminated string.

---

### Post by Bachstelze on 2013-02-15
> **jwbrase said:**
> Yes, although "NULL" in C refers to the null pointer value (which is zero on most systems, hence the name). '\0' is the ASCII/Unicode null character.

"The null pointer value" is nonsensical. NULL is a macro that expands to a null pointer constant. A null pointer constant is either an integer constant with value 0, or such a constant cast to a void*.

---

### Post by Bachstelze on 2013-02-15
> **ofnuts said:**
> But the most questionable thing in your code is using "\n" at the beginning of the format strings.... (am I starting a religious war here?). One reason is that when the output is a "tty", things get flushed/displayed by the C runtime only when it sees a "\n". So with code like this:

```

printf("\nline1");
// some code runs here
printf("\nline2");
// some code breaks here
printf("\nline3");

```
You will only see "line1" on your terminal and thus you will search a problem between  "line1" and "line2" while the problem is really between "line2" and "line3".

He has been told that several times already, by me and others. But as usual, he never listens...

---

### Post by Tony Flury on 2013-02-15
> **r-senior said:**
> If you have an array of 10 char, str[10] is the eleventh char and is beyond the space allocated for the string. The ten characters of the string are indexed 0 to 9.

So, yes, you do need to make sure the last character of the string is the null character '\0', but that would be str[9] rather than str[10].

IAMTUBBY - please - for your homework tonight write out 100 times - in C array indexes start at zero - so char str[10] has members str[0] to str[9] **only**. In null terminated strings the '/0' has to stored between str[0] and str[9].

*I know for a fact you have been told this already several times, yet you persist in the same error. Getting it wrong in anything other than trivial code can be disastrous.*

---

### Post by r-senior on 2013-02-15
+1

String manipulation and correct termination is a critical part of programming in C and something every beginner should devote plenty of effort to mastering.

Perhaps better than writing it out though would be a to write a program that makes an array of 100 char arrays of 10 chars, each filled with a properly terminated string.

Bachstelze will be marking it so make it good.

---

### Post by IAMTubby on 2013-02-16
Thanks everyone for the replies :)
I am extremely sorry for not following the advice especially about newline characters. I promise never to repeat in future. Special mention for Bachstelze who has told me of this more than once. Sorry Sir.

In this program, I have taken care of the following
1. null termination
2. newline character at the end
3. Indentation, as mentioned by r-senior on another thread.

_Output_
[b][rl?] : [Sir, I have tried, I really hope I get this right.]
[Tony Flury] : [Sir, yes, I'm sorry, I have been stubborn on my bad practices(unintentionally). I promise you won't have a complaint after I get this one right.]
[Bachstelze] : [Bachstelze, sorry, this is the last time I'm making same mistakes again and again. I'm sorry Sir]
[spjackson] : [spjackson, From this program onwards, I'll never put the newline character at the beginning of the line]
[ofnuts] : [Yes sir, shall take care of string's null termination using memset, and newline character mistakes from today onwards.]
[jwbrase] : [thanks jwbrase, shall remember that]
[Some Penguin] : [okay, thanks for the reply.]
[/b]

_code_
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void)
{
 char myarray[100][10];
 char mentors[][30] = {"r-senior","Tony Flury","Bachstelze","spjackson","ofnuts","jwbrase","Some Penguin"};
 char myresponse [][150] = {"Sir, I have tried, I really hope I get this right.","Sir, yes, I'm sorry, I have been stubborn on my bad practices(unintentionally). I promise you won't have a complaint after I get this one right.","Bachstelze :), sorry, this is the last time I'm making same mistakes again and again. I'm sorry Sir","spjackson, From this program onwards, I'll never put the newline character at the beginning of the line","Yes sir, shall take care of string's null termination using memset, and newline character mistakes from today onwards.","thanks jwbrase, shall remember that","okay, thanks for the reply."};
 int i =0;

 /* this is only to demonstrate that i can now populate an array and take care of NULL termination */
 for(i=0;i<=100;i++)
 {
        memset(myarray[i],'\0',sizeof(myarray[i]));
        strcpy(myarray[i],"hello worl?");
 }

 /* This is to demonstrate my use of newline character at the end*/
 for(i=0;i<=6;i++)
 {
        printf("[%s] : [%s]\n",mentors[i],myresponse[i]);
 }

 return 0;
}

```

_questions_
1. I have no idea why the name **r-senior** is getting replaced by **rl?** after I define **hello worl?** for myarray.
2. Please forgive me until this thread is "SOLVED" for mistakes relating to arrays. I shall not repeat any of the previous ones, or the ones to come from your replies from today onwards.
3. If I intialize an array as char str[30] = "123"; and fill only 3 characters out of the 30, the rest 27 are initialized  to 0 correct? (I tried it out by printing, just confirming)

Thanks.

---

### Post by dwhitney67 on 2013-02-16
You have a bug here:
```

for(i=0;i<=100;i++)

```
If an array has a size of 100, then you index using values 0 through 99.  You're using 100 above as the final index.

How about mitigating any silly errors by defining the size up-front, so that you don't hard-code values in the code?
```

#define MAX_ITEMS   100
#define MAX_STR_SZ   10
...
char myarray[MAX_ITEMS][MAX_STR_SZ];
...
for (int i = 0; i < MAX_ITEMS; ++i)     // C99 style
{
   ...
}
...

```

P.S.  Alternatively, and I must admit that this is ugly, you could do something like:
```

char myarray[100][10];
...
const size_t arraySize = sizeof(myarray) / sizeof(char[10]);

for (int i = 0; i < arraySize; ++i)
{
    ...
}

```

---

### Post by r-senior on 2013-02-16
... and another here:

```
strcpy(myarray[i],"hello worl?");
```

The elements in the array 'myarray' are 10 chars but you copy 11 chars into it. You should copy no more than 9 so that there is space for the '\0'. (You should really consider using strncpy rather than strcpy to avoid the overflow).

So, following on from dwhitney67's #defines:

```
strncpy(myarray[i], "hello worl?", MAX_STR_SZ - 1);
```

EDIT: My name looks like it is getting corrupted by these overflows. At least this is a good example of why all this stuff is important.

---

### Post by IAMTubby on 2013-02-16
> **dwhitney67 said:**
> You have a bug here:
```

for(i=0;i<=100;i++)

```
If an array has a size of 100, then you index using values 0 through 99.  You're using 100 above as the final index.

dwhitney67, thanks a lot for pointing it out. I'm sorry but that was a typo and not a mistake in understanding. 
Bachstelze, if you are reading this, sorry, I haven't made the mistake again, I promise that was a typo.

> **r-senior said:**
> ... and another here:

```
strcpy(myarray[i],"hello worl?");
```

The elements in the array 'myarray' are 10 chars but you copy 11 chars into it. You should copy no more than 9 so that there is space for the '\0'.
absolutely Sir, corrected it, please find the corrected code and o/p.
```

#include <stdio.h>
#include <string.h>

#define MAX_ITEMS   100
#define MAX_STR_SZ   10

int main(void)
{
 char myarray[MAX_ITEMS][MAX_STR_SZ];
 char mentors[][MAX_STR_SZ*5] = {"r-senior","Tony Flury","Bachstelze","spjackson","ofnuts","jwbrase","Some Penguin"};
 char myresponse [][MAX_STR_SZ*15] = {"Sir, I have tried, I really hope I get this right.","Sir, yes, I'm sorry, I have been stubborn on my bad practices(unintentionally). I promise you won't have a complaint after I get this one right.","Bachstelze :), sorry, this is the last time I'm making same mistakes again and again. I'm sorry Sir","spjackson, From this program onwards, I'll never put the newline character at the beginning of the line","Yes sir, shall take care of string's null termination using memset, and newline character mistakes from today onwards.","thanks jwbrase, shall remember that","okay, thanks for the reply."}; 

 int i =0;
 
 for(i=0;i<MAX_ITEMS;i++)
 {
   memset(myarray[i],'\0',sizeof(myarray[i]));
   strncpy(myarray[i], "hello worl?", MAX_STR_SZ - 1);
 }

 for(i=0;i<MAX_ITEMS;i++)
   printf("myarray[%d] == [%s]\n",i,myarray[i]);

 for(i=0; i< sizeof(mentors)/sizeof(mentors[0]);i++)
 {
  printf("[%s] : [%s]\n",mentors[i],myresponse[i]);
 }
 
 
 return 0;
}
```

_output_
[b]
myarray[0] == [hello wor]
myarray[1] == [hello wor]
..
myarray[99] == [hello wor]
[r-senior] : [Sir, I have tried, I really hope I get this right.]
[Tony Flury] : [Sir, yes, I'm sorry, I have been stubborn on my bad practices(unintentionally). I promise you won't have a complaint after I get this one right.]
[Bachstelze] : [Bachstelze :), sorry, this is the last time I'm making same mistakes again and again. I'm sorry Sir]
[spjackson] : [spjackson, From this program onwards, I'll never put the newline character at the beginning of the line]
[ofnuts] : [Yes sir, shall take care of string's null termination using memset, and newline character mistakes from today onwards.]
[jwbrase] : [thanks jwbrase, shall remember that]
[Some Penguin] : [okay, thanks for the reply.][/b]

---

### Post by ofnuts on 2013-02-16
Unless there is good reason to believe that:

[LIST=1]
[*]Your mentors names are 5 times longer than some arbitrary limit
[*]Your answer to them is 3 times longer than their name limit
[/LIST]
Don't use things like "MAX_STR_SZ*5" or "MAX_STR_SZ*15". This makes things appear related when they are not. Instead:
```

#define MAX_MENTOR_NAME_SZ 20
#define MAX_ANSWER_SZ 100

```Now of course in real life these two arrays would be plain array of strings and you wouldn't need these arbitrary limits:
```

char *mentors[]=
{"r-senior","Tony Flury","Bachstelze","spjackson","ofnuts","jwbrase","Some Penguin"};

```

---

### Post by spjackson on 2013-02-16
> **IAMTubby said:**
> 
3. If I intialize an array as char str[30] = "123"; and fill only 3 characters out of the 30, the rest 27 are initialized  to 0 correct? (I tried it out by printing, just confirming)

Er, yes... Trying it by printing is ok, but observing what happens now in one context would not be sufficient itself for you to rely on that behaviour. However, the language standard does indeed guarantee this behaviour, and that is why you can rely on it.

To be pedantic, "123" is a string literal of length 4, not 3. You are explicitly initialising elements 0-3, and elements 4-29 are implicitly intialised (with zeroes).

---

### Post by Bachstelze on 2013-02-16
> **spjackson said:**
> 
To be pedantic, "123" is a string literal of length 4, not 3.

To be super-pedantic, the *length* of a string (as returned by e.g. *strlen()*) does not include the terminating null byte. Its *size* does.

---

### Post by spjackson on 2013-02-16
> **Bachstelze said:**
> To be super-pedantic, the *length* of a string (as returned by e.g. *strlen()*) does not include the terminating null byte. Its *size* does.
I definitely didn't mean size. Arrays have a **length**, which is the number of elements they contain. (See for example "variable **length** arrays".) They also have a size, which is the number of bytes they contain. I definitely meant the number of array elements, not the **size** of the array. Because we are talking about a string literal which is an array of character, the length of the array is also its size. If it was a wide string literal, this would not be the case.

The length returned by strlen would indeed be 3, but 3 is the length of the string "123", not the length of the character array "123" (for differing meanings of length).

So, I do stand corrected. I should have said, '"123" is a string literal which is an array of character of length 4, not 3'.

In any event, the point is that str[3] is explicitly initialised to the null byte supplied in the initialiser, and str[4] through str[29] are implicitly initialised to zero, according to the rules of aggregate initialisation.

And now I'll go and figure out how many angels can dance on the head of a pin. ;-)

---

