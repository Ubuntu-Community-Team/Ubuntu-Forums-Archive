---
title: "strings in c"
date: 2010-04-12
forum: Programming Talk
---

### Post by kartabosh on 2010-04-12
[PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char s[],x[],y[];
char decode(char*);
int main(){
	while (1){
		s[0]='A';
		printf("> ");
		gets(x);
		decode(*x);
//		printf("%s",x);
//		printf("%s",y);
		if (strcmp(x,"exit")==0) break;
		
		printf("\n");
	}
	return 0;	
}
char decode(char *x){
int w,wi;	
	for (w=0;w<strlen(x);++w) {
		switch(x[w]){
				case 'a'...'z':y[wi]=x[w];++wi;break;
				case '0'...'9':y[wi]=x[w];++wi;break;
				default: printf("error");
		}
	}
}
[/PHP]

i really hate strings in c
can anyone tell me what i'm doing wrong?

---

### Post by Simian Man on 2010-04-12
None of the strings you declare have any sizes.  In C you must allocate space for your strings somewhere.  Right now you are declaring strings of size 0 so when you try to use them something bad will happen.  Try declaring a size for your strings like:
```
char s[64],x[64],y[64]; 
```

This allocates global strings of 64 characters each giving you some space to put characters.

Though even that is far from ideal because, for one they're global variables, and secondly because if the user types in more than 64 characters, your program will happily enter the realm of undefined behaviour.

C is a pain to work with for anything, but text work is especially bad.  What are you doing and do you need C?

---

### Post by kartabosh on 2010-04-12
i did give them sizes and still not working

i don't really need c its the only thing i know how to use up to now

---

### Post by MadCow108 on 2010-04-12
this
decode(*x);
and this
char decode(char *x){

does not fit together

=> skip the dereference in the call
and wi is not initialized
if you compile with -Wall the compiler will even warn about both errors

also never use gets (it even says in the manpage)
use fgets instead

---

### Post by kartabosh on 2010-04-12
[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char s[64],x[64],y[64];
char decode(char*);
int main(){
	while (1){
		s[0]='A';
		printf("> ");
		gets(x);
		decode(x);
//		printf("%s",x);
//		printf("%s",y);
		if (strcmp(x,"exit")==0) break;
		
		printf("\n");
	}
	return 0;	
}
char decode(char *x){
int w,wi;	
	for (w=0;w<strlen(x);++w) {
		switch(x[w]){
				case 'a'...'z':y[wi]=x[w];++wi;break;
				case '0'...'9':y[wi]=x[w];++wi;break;
				default: printf("error");
		}
	}
}
[/PHP]

same error
gets works for me

---

### Post by lisati on 2010-04-12
Although I don't think it's likely to be a major issue in this program, don't forget to allow for the zero byte to terminate the string.

---

### Post by kartabosh on 2010-04-12
well the problem is encountered in calling the function not in displaying the string things

---

### Post by MadCow108 on 2010-04-12
wi is still uninitialized

also your decode function does nothing, is that intentional?

---

### Post by kartabosh on 2010-04-12
[PHP]#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char s[64],x[64],y[64];
char decode(char*);
int main(){
	while (1){
		s[0]='A';
		printf("> ");
		gets(x);
		decode(x);
//		printf("%s",x);
		printf("%s",y);
		if (strcmp(x,"exit")==0) break;
		
		printf("\n");
	}
	return 0;	
}
char decode(char *x){
int w,gicu=0,wi=0;	
	for (w=0;w<strlen(x);++w) {
		if (gicu==0){
		switch(x[w]){
				case 'a'...'z':y[wi]=x[w];++wi;break;
				case '0'...'9':y[wi]=x[w];++wi;break;
				default: ++gicu;break;	
		}
		}
	}
}
[/PHP]

well it works now
quick thinking madcow i forgot to initialize wi 
also the function modifies the strings which are global

alexander@amd64:~/1$ ./1
> ilon paiva
ilon
> exit
exitalexander@amd64:~/1$


i am working on a much bigger program but the first part of it was to decode a word so you can't really crash my program
thats why i used gets and not %s 
thanks for your help

---

### Post by kartabosh on 2010-04-12
yet another error 

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char s[64],x[64],y[64];
int decode(char*);
int main(){
int error;	
	while (1){
		for (error=0;error<65;++error) y[error]=''; // here's the error
		error=0;
		s[0]='A';
		printf("> ");
		gets(x);
		if(decode(x)!=0) printf("error\n");
		
		printf("%s",y);
		if (strcmp(x,"exit")==0) break;
		
		printf("\n");
	}
	return 0;	
}
int decode(char *x){
int w,gicu=0,wi=0;	
	for (w=0;w<strlen(x);++w) {
		if (gicu==0){
		switch(x[w]){
				case 'a'...'z':y[wi]=x[w];++wi;break;
				case '0'...'9':y[wi]=x[w];++wi;break;
				default: ++gicu;break;	
		}
		}
	}
return gicu;
}
[/PHP]

how do you empty the string?

---

### Post by Simian Man on 2010-04-12
> **kartabosh said:**
> i don't really need c its the only thing i know how to use up to now

No offense, but I don't think you know enough C for this to be a good reason to use it.  Whatever it is you are trying to do will be much easier with Python and your Python knowledge will outstrip your C knowledge after reading one tutorial.

---

### Post by lisati on 2010-04-12
> **kartabosh said:**
> 

how do you empty the string?

I'll answer this question with a question: how are strings stored in C? (Hint: see my previous post in this thread)

---

### Post by kartabosh on 2010-04-12
> **Simian Man said:**
> No offense, but I don't think you know enough C for this to be a good reason to use it.  Whatever it is you are trying to do will be much easier with Python and your Python knowledge will outstrip your C knowledge after reading one tutorial.

of course i dont know enough c, i am a beginner, a newbie, a total novice 
at school the first thing we programmed in was c so thats what i know, i don't know much but it is what i know

---

### Post by kartabosh on 2010-04-12
> **lisati said:**
> I'll answer this question with a question: how are strings stored in C? (Hint: see my previous post in this thread)

i know strings are chars that end in "\0" but what does that help with?

---

### Post by kartabosh on 2010-04-12
is this recommended?
for (error=62;error>0;--error) y[error]='\0';

---

### Post by lisati on 2010-04-12
> **kartabosh said:**
> i know strings are chars that end in "\0" but what does that help with?
You asked how to empty a string. The quick and easy way is something like this:
```
string_var[0]=0x00;
```

---

### Post by kartabosh on 2010-04-12
> **lisati said:**
> You asked how to empty a string. The quick and easy way is something like this:
```
string_var[0]=0x00;
```

that doesn't really work
look:
> ilon paiva
error
ilon
> ila
ilan

---

### Post by kartabosh on 2010-04-12
fixed it with 
[PHP]
int decode(char *x){
int w,gicu=0,wi=0;	
	for (w=0;w<=strlen(x);++w) {
		if (gicu==0){
		switch(x[w]){
				case 'a'...'z':y[wi]=x[w];++wi;break;
				case '0'...'9':y[wi]=x[w];++wi;break;
				case '\0':y[wi]=x[w];++wi;break;
				default: ++gicu;break;	
		}
		}
	}
return gicu;
}
[/PHP]

---

### Post by phrostbyte on 2010-04-12
This is very inefficient loop, because strlen(x) is O(n) operation, and you are repeating it n times, so it is O(n^2) for no good reason.

for (w=0;w<strlen(x);++w) { 

change to

for (w=0; x[w]; ++w) {

---

### Post by azagaros on 2010-04-12
Strings in C...

```

Char *pString;  // a pointer to a string....
pString = (char*)malloc(20);   // we need to allocate some space for my string
pString++;      // moves through a string....
char c = *pString;        // returns the character at pString.
while (++pString != 0)
{
    // this will search through the string 
    char c= *pString;
    // do work with c, like
    if(*pString == 'a')
    {
       // do something
    }
} 

Char cString[20];  // this allocates an array base 0 length 20 ie 0 to 19.
*cString++;  // moves through the string.
char c = cString[10];  // returns the character at position 10

int nIndex = 0;
while(nIndex < 20)
{
     char c = cString[nIndex];
     // do work with character
     nIndex++;
}

```

I hope that provides some insight to what you are doing. 
I understand the frustration of the abstraction between the two ways to do strings in C.

I didn't fill the strings with anything.

---

### Post by kartabosh on 2010-04-12
> **phrostbyte said:**
> This is very inefficient loop, because strlen(x) is O(n) operation, and you are repeating it n times, so it is O(n^2) for no good reason.

for (w=0;w<strlen(x);++w) { 

change to

for (w=0; x[w]; ++w) {

thx for the hint
i usually set a variable to strlen(x) so it wont compute it n times, just once and this is one operation short

---

### Post by kartabosh on 2010-04-12
> **azagaros said:**
> Strings in C...

```

Char *pString;  // a pointer to a string....
pString = (char*)malloc(20);   // we need to allocate some space for my string
pString++;      // moves through a string....
char c = *pString;        // returns the character at pString.
while (++pString != 0)
{
    // this will search through the string 
    char c= *pString;
    // do work with c, like
    if(*pString == 'a')
    {
       // do something
    }
} 

Char cString[20];  // this allocates an array base 0 length 20 ie 0 to 19.
*cString++;  // moves through the string.
char c = cString[10];  // returns the character at position 10

int nIndex = 0;
while(nIndex < 20)
{
     char c = cString[nIndex];
     // do work with character
     nIndex++;
}

```

I hope that provides some insight to what you are doing. 
I understand the frustration of the abstraction between the two ways to do strings in C.

I didn't fill the strings with anything.

i don't really know how to use pointers yet so you can probably understand how that code can be confusing to me

---

### Post by lisati on 2010-04-12
> **azagaros said:**
> I understand the frustration of the abstraction between the two ways to do strings in C.

+1. I was contemplating on expanding the reply I gave to include a bit about looping through the string. :)

---

### Post by lisati on 2010-04-12
> **kartabosh said:**
> i don't really know how to use pointers yet so you can probably understand how that code can be confusing to me

I can appreciate your frustration - it took me a little while to get my head round pointers, and often there's more than one way of solving a problem. Hang in there, it will get easier with practice.

---

### Post by phrostbyte on 2010-04-12
You make want to look into C++. Strings are kind of easier (and safer?) to work with in the language. Of course languages like Python are even better, since they remove all the nasty details of memory management from the programmer, and have nicer syntax to boot (IMO). The only time I would do C is if I am writing a library that I intend to call from some other language, that's where C really shines (everyone can call it).

---

### Post by kartabosh on 2010-04-12
i tried working in c++ and i should try harder because in two months i have a programming exam under c++ so i thought i would stick to c until i understand programming a bit more

---

### Post by azagaros on 2010-04-12
Confusion about pointers?

First thing to remember in C everything is a pointer of some form.  It just depends in how you access it or want to access it.  Also how you want to memory manage it.

```

char c = 'a';  // a literal 
*c  //  a pointer to that literal.
&c  // a reference to c. 

```

C++ isn't much different but it uses different forms of allocation to get the same things done, pointers are the same in C++.

---

### Post by nvteighen on 2010-04-12
> **kartabosh said:**
> i tried working in c++ and i should try harder because in two months i have a programming exam under c++ so i thought i would stick to c until i understand programming a bit more

Hmm... the issue is that the benefits of C++ are clear just for people that have much more experience in programming... C++ is a higher-level language (i.e. less near to the machine internals like, e.g. C) that took the goal to also be somewhat backwards compatible to C... The thing is that you get the idea of why C++ is like it is by knowing C; you can learn C++ without knowing C, but in that case you won't totally understand it.

I'll suggest you the same as others already told you: take a look at Python. Ok, the syntax is different, but it's a much nicer language to understand the general thought processes related to programming. I think learning how to program in a different language will prove to be more productive than trying to tackle down a language in which you don't actually understand with what general programming concepts your playing around.

This doesn't mean you should stop learning C at all, of course!

If you're using Ubuntu and interested, you'll find Python preinstalled; look at the stickies for information on tutorials and guides (well, not only for Python, but C and C++ too).

---

### Post by kartabosh on 2010-04-12
i used python, i even had an exam on python and c and i found c to be more interesting than python
here's another problem 
what i am trying to do at this point is to read starea which is a string that keeps in the last state that the read thing was 
the initial state is A 
and i am trying to get to B or AB using a map
A0A if state is A and the read number is 0 add to the temporary state the letter A
A1A if state is A and the read number is 1 add to the temporary state the letter A
A1B if state is A and the read number is 0 add to the temporary state the letter B
B1B if state is B and the read number is 1 add to the temporary state the letter B

so if state is A and i type in 1 the output should be AB

i'm stuck here
[PHP]
int FengShui(char s){
int w,nintendo;
nintendo=strlen(starea);
	for (w=0; w<=nintendo; ++w) {
		if (starea[w]=='A'){
				if (s=='0'){ printf("add A"); starea[w]='A';}
				if (s=='1'){ printf("add A"); starea[w]='A';}
				if (s=='1'){ printf("add B"); starea[w]='B';}
				//else eroare;
		}
		if (starea[w]=='B'){
				if (s=='0'){ printf("error"); starea[w]='B';}
				if (s=='1'){ printf("add B"); starea[w]='B';}
				//else eroare;
		}
	}
return 0;
}[/PHP]

---

### Post by kartabosh on 2010-04-12
speaking about python in python i could of done something like
if (s=='0') l.append='A';
if (s=='1') l.append='A'; l.append='B'
or something like that i don't remember but how do i do that in C

---

### Post by MadCow108 on 2010-04-12
strcat is what comes closest, but you have to make sure there is enough memory
better use strncat to make sure you don't introduce dangerous bugs

---

### Post by kartabosh on 2010-04-13
p.s. strcpy(string, " "); is a fast way "empty" a string

---

### Post by kartabosh on 2010-04-13
trying to improve my code now i get a segmentation error
[PHP]int decode(char *x){
int w,gicu=0;
	for (w=0; x[w]; ++w) {
		if (gicu==0){
		switch(x[w]){
				case 'a'...'z':
				case '0'...'9':
				case '\0':strcat(y,x[w]);break;
				default: ++gicu;break;	
		}
		}
	}
return gicu;
}[/PHP]

---

### Post by Compyx on 2010-04-13
You pass an int as the second argument to strcat(), but strcat() expects a const char *. Leave out the subscript like this:
```

strcat(y, x);

```
As others have pointed out, either make damn sure you have enough room in y to use strcat, or use strncat().

Also try passing some extra flags to gcc: '-Wall -Wextra -pedantic'. I personally prefer to use '-ansi' or '-std=c89' as well, but since you're using GCC-specific extension, you can't use that (case 'a'...'z' is GNU-C, not standard C).

---

### Post by kartabosh on 2010-04-13
well that works but not really good, i think i should stick to the normal y[i]=x[ii] or something

---

### Post by kartabosh on 2010-04-14
> **Compyx said:**
> You pass an int as the second argument to strcat(), but strcat() expects a const char *. Leave out the subscript like this:
```

strcat(y, x);

```
As others have pointed out, either make damn sure you have enough room in y to use strcat, or use strncat().

Also try passing some extra flags to gcc: '-Wall -Wextra -pedantic'. I personally prefer to use '-ansi' or '-std=c89' as well, but since you're using GCC-specific extension, you can't use that (case 'a'...'z' is GNU-C, not standard C).

i don't really want to copy the whole x in the new string just some chars

---

### Post by Compyx on 2010-04-14
Then you can use strncat(), you can tell strncat() how many characters you want to copy. Just keep in mind that strncat writes a '\0' after the characters copied, so if you tell strncat() to copy 4 characters you must make sure you have room for 4 + 1 = 5 characters.

---

### Post by kartabosh on 2010-04-15
> **Compyx said:**
> Then you can use strncat(), you can tell strncat() how many characters you want to copy. Just keep in mind that strncat writes a '\0' after the characters copied, so if you tell strncat() to copy 4 characters you must make sure you have room for 4 + 1 = 5 characters.

yes, but i don't want to copy the all characters it might be the first, third and fourth, or second, fifth and ninth not some chars in a row

---

### Post by Compyx on 2010-04-15
[php]
char *decode(char *x)
{
    char *y;
    size_t i;
    size_t k;

    /* allocate enough storage for y to hold all characters in x, in case
     * we only find characters we want */
    y = malloc(strlen(x) + 1);
    if (y == NULL) {
        /* malloc failed, report */
        fprintf(stderr, "%s:%d: failed to allocate %lu bytes\n",
            __FILE__, __LINE__, (unsigned long)(strlen(x) + 1));
        return NULL;
    }

    /* k is the index in the result string */
    k = 0;
    /* iterate string x */
    for (i = 0; x[i] != '\0'; i++) {
        /* decide what we want to do with x[i] */
        switch (x[i]) {
            case 'a'...'z':
            case '0'...'9':
                /* store x[i] in y */
                y[k++] = x[i];
                break;
            default:
                /* no nothing */
        }
     }
     /* properly terminate y */
     y[k] = '\0';

     /* return pointer to 'decoded' string */     
     return y;
}
[/php]

This will return a 'decoded' string. The logic that decides if a character should be stored in the result is in the switch statement. You can of course add your own logic.

The point is the use of two indexes, one for the input string and one for the result string. Whenever you grab a character from the input string and decide you want to copy it, you store that character in the result string and increment the index in the result string.

I used malloc() in my example to make sure the result string is large enough to avoid overflow. If you want to use a global result string 'y', you can leave out the malloc call and the error handling, something like this: 

[php]
void decode(char *x)
{
    size_t i;
    size_t k;

    /* k is the index in the result string */
    k = 0;
    /* iterate string x */
    for (i = 0; x[i] != '\0'; i++) {
        /* decide what we want to do with x[i] */
        switch (x[i]) {
            case 'a'...'z':
            case '0'...'9':
                /* store x[i] in y */
                y[k++] = x[i];
                break;
            default:
                /* no nothing */
        }
     }
     /* properly terminate y */
     y[k] = '\0';
}
[/php]

---

### Post by kartabosh on 2010-04-15
thanks, i'll post when i get other errors

---

### Post by kartabosh on 2010-04-15
is there an official c for "if 'c' not in string {" ?

---

### Post by azagaros on 2010-04-15
yes,e

it is in the string functions of c and c++.  

[php]
include <string.h>

char cSearch = 'c';
char cSearchStr = "This is a search string";

char *nPos = strchr(cSearchString, cSearch);
if(nPos)
{
    // found you :)
}
[/php]

a useful list of the c string functions are at 
[http://www.edcc.edu/faculty/paul.bladek/c_string_functions.htm](http://www.edcc.edu/faculty/paul.bladek/c_string_functions.htm)

every language usually has these kind of functions.  In c++ these are a little different but they basically use this set.

---

### Post by kartabosh on 2010-04-15
> **azagaros said:**
> yes,e

it is in the string functions of c and c++.  

[php]
include <string.h>

char cSearch = 'c';
char cSearchStr = "This is a search string";

char *nPos = strchr(cSearchString, cSearch);
if(nPos)
{
    // found you :)
}
[/php]

a useful list of the c string functions are at 
[http://www.edcc.edu/faculty/paul.bladek/c_string_functions.htm](http://www.edcc.edu/faculty/paul.bladek/c_string_functions.htm)

every language usually has these kind of functions.  In c++ these are a little different but they basically use this set.
 thanks, now can you explain to me exactly what it does

---

### Post by MadCow108 on 2010-04-15
if you can't tell from the code how about reading the link?...

if you still don't get it read the manpage
man function
(you need manpages-dev installed)

---

### Post by azagaros on 2010-04-15
ok.

The function strchr returns a character pointer to a position in the string, if the pointer is 0; it didn't find it.

[php]
char *pChar = strchr(cSearchstr, cSearch);
if(!pChar)
{
    // I didn't find anything in my search string
}
else
{
   // I found you at...
   printf("I found %c at %l", cSearch, (long)(pChar-*cSearchstr));
}
[/php]

I hope that helps to some extent.

---

### Post by kartabosh on 2010-04-16
thank you again

---

### Post by Compyx on 2010-04-16
> **azagaros said:**
> yes,e
[php]
char cSearch = 'c';
char cSearchStr = "This is a search string";
[/php]


That should be:
[php]
int cSearch = 'c';
char cSearchStr[] = "This is a search string";
/* or char *cSearchStr, if you don't intend to manipulate cSearchStr. */
[/php]
A character literal is of type int. A C-style string is either declared char[] or char *.

> **azagaros]
[php]
printf("I found %c at %l", cSearch, (long)(pChar-*cSearchstr)) said:**
> 

and that should be:
[php]
printf("I found %c at %ld\n", cSearch, (long)(pChar - cSearchStr));
[/php]
%l is a length specifier which cannot stand on its own, it needs a format specifier to go with it, such as 'd', 'u' or 'x'.
Also, don't dereference cSearchStr.

---

### Post by kartabosh on 2010-04-16
so basically the unofficial 'if x not in mystring' could be something like
[PHP]if (strchr(mystring,'x'));
  else printf ("no x's found\n");[/PHP]

---

