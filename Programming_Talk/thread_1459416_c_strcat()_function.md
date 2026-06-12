---
title: "c strcat() function"
date: 2010-04-21
forum: Programming Talk
---

### Post by kartabosh on 2010-04-21
can anyone tell me why this code 
[PHP]
#include <stdio.h>
#include <string.h>
char s[60];
char s2[60];
int main(){
int i;
gets(s);
printf("%d\n",strlen(s));
for (i=0;s[i];++i){
    strcat(s2,&s[i]);
}
printf("%s\n",s2);
return 0;
}
[/PHP]
returns this
```
ilon
4
ilonlononn
```

and why this short variation of it 
[PHP]#include <stdio.h>
#include <string.h>
char s[60];
char s2[60];
char zorro;
int main(){
int i;
gets(s);
printf("%d\n",strlen(s));
for (i=0;s[i];++i){
    zorro=s[i];
    strcat(s2,&zorro);
}
printf("%s\n",s2);
return 0;
}
[/PHP]
returns the good answer? must there always be that extra assignment or is there a shorter way??

---

### Post by MadCow108 on 2010-04-21
they are both wrong
strcat concatenates two cstyle strings = null terminated strings
that mean it adds all characters after the null in the first string until it finds the null in the second string.
So the first variant gives the result I consider good (if it where correct).

s2 is never initialized so it may be that there is no null in the beginning!
set the first byte to zero before you use it:
s2[0] = 0;

in the second case its even worse. A single char is no cstyle string.
There is no guarantee that there is a nullbyte behind it
you have to do that:
char tmp[2];
tmp[0]=z[i];
tmp[1] = 0;

(it works in your case because the variables are global, which means they are placed in the bss section which is filled with zeros, but don't count on that! Even if it is so, it will fail when zorro gets placed in the last byte of the bss)

also it is terrible inefficient because every strcat must iterate the first string again.
and as the compiler tells you: never use gets! fgets is better

---

### Post by kartabosh on 2010-04-21
> **MadCow108 said:**
> 
also it is terrible inefficient because every strcat must iterate the first string again.
and as the compiler tells you: never use gets! fgets is better
i don't know how to use fgets
this looks really strange 
 char *fgets( char *str, int num, FILE *stream ); 	 is it better to use
```
for(..){
 tempstring[n]=x[i]; 
++n}
tempstring[n]='\0'
```
?

---

### Post by MadCow108 on 2010-04-21
char *fgets( char *str, int num, FILE *stream );
str is the buffer you want to save the input, num is the size of the buffer (or max amount of chars you want to read from a line - 1 [for the null termination]) and stream is the stream you want to read from
```

char buffer[1024];
fgets(buffer, 1024, stdin);

```

this ensures there is no buffer overflow and you recieve a valid c style string.
Of course you can use gets for private testing code, but never ever use it in code someone other than you might be using.



what do you actually want to do?
copy a string?
why not use strcpy (or better the safer strncpy)

---

### Post by kartabosh on 2010-04-21
i dont want to copy a string i was just testing it, i want to copy certain letters from strings into other ones in random order 
i'm a beginner programmer as you may have already noticed so i just try to implement random stuff, now i'm trying to do the normal expression to rpn 
input: a+b-c
output: a b c - +

---

### Post by trent.josephsen on 2010-04-21
> **kartabosh said:**
> i dont want to copy a string i was just testing it, i want to copy certain letters from strings into other ones in random order 
i'm a beginner programmer as you may have already noticed so i just try to implement random stuff, now i'm trying to do the normal expression to rpn 
input: a+b-c
output: a b c - +

You won't be able to copy single characters to the end of a string with strcat.  (In any case you should almost always use strncat to avoid accidental buffer overflow.)

Use fgets to get a string containing the entire expression ("a + b - c") and use strtok to pick it apart.  Never use gets.  Be careful with strtok; it can require some thought to get right.

---

### Post by MadCow108 on 2010-04-21
> You won't be able to copy single characters to the end of a string with strcat. (In any case you should almost always use strncat to avoid accidental buffer overflow.)
yes you can
you just have to convert the single character to a string containing only one character (+ null)
its shown above.
But its not the best of ideas to do it that way

---

### Post by kartabosh on 2010-04-21
thank you for your advice, so is the individual copying good? 
and how does the strtok work

---

### Post by MadCow108 on 2010-04-21
there is an example in the manpage
man strtok
(assuming you have manpages-dev installed)

It is a bit more advanced function and it is used differently than most of the rest of the C standard library (it has an internal global state)
I recommend having a look at later it when you have a better understanding of the language

---

### Post by trent.josephsen on 2010-04-21
> **MadCow108 said:**
> yes you can
you just have to convert the single character to a string containing only one character (+ null)
its shown above.
But its not the best of ideas to do it that way

Then you're not copying a character, but a string.  The fact that the string happens to be of length 1 is of no consequence (and having to copy a char into a 2-element char[] is not only hideous and awkward but also tells you that you're doing it wrong).  Nevertheless, I think we're on the same page, so I'll not continue.

There are good resources available for strtok (I won't go into it here).  Manpages are good, but you should also look in a C book if you have one.  K&R 2 describes it briefly on page 250.  But really, just know that you won't get it right on the first try.

---

### Post by kartabosh on 2010-04-22
> **trent.josephsen said:**
> Then you're not copying a character, but a string.  The fact that the string happens to be of length 1 is of no consequence (and having to copy a char into a 2-element char[] is not only hideous and awkward but also tells you that you're doing it wrong).  Nevertheless, I think we're on the same page, so I'll not continue.

There are good resources available for strtok (I won't go into it here).  Manpages are good, but you should also look in a C book if you have one.  K&R 2 describes it briefly on page 250.  But really, just know that you won't get it right on the first try.
k&r is too advanced for me

---

### Post by trent.josephsen on 2010-04-22
> **kartabosh said:**
> k&r is too advanced for me

Not surprising.  I was a skilled Python and Java programmer before I started K&R (and even so it makes a few references to tools and languages that were before my time).  But you should be able to find help on strtok in any C book worth half the money you pay for it.  (Corollary: if any C book doesn't contain a description of strtok, then you overpaid by at least 100%.)

I don't know, and can't tell at the moment, what manpage Ubuntu has for strtok, but the one at [http://linux.die.net/man/3/strtok](http://linux.die.net/man/3/strtok) seems reasonably written and contains an example that you should be able to follow.

---

### Post by stchman on 2010-04-22
Why would you perform a strcat on s2 with the ADDRESS of each of s elements?

If s was initialized with say "HELLO_THERE" then the following:

strcat( s2, s );

s2 would have the value of "HELLO_THERE".

It would have been far easier just to do this:

[PHP]

#include <stdio.h>
#include <string.h>

char s[60];
char s2[60];

int main()
{
    int i = 0;
    gets( s );
    printf( "%d\n", strlen( s ) );
    strcat( s2, s );
    printf("%s\n",s2);
    return 0;
}  
[/PHP]

The strcat functions will concatenate and ENTIRE character array.

---

### Post by kartabosh on 2010-04-23
> **stchman said:**
> Why would you perform a strcat on s2 with the ADDRESS of each of s elements?

If s was initialized with say "HELLO_THERE" then the following:

strcat( s2, s );

s2 would have the value of "HELLO_THERE".

It would have been far easier just to do this:

[PHP]

#include <stdio.h>
#include <string.h>

char s[60];
char s2[60];

int main()
{
    int i = 0;
    gets( s );
    printf( "%d\n", strlen( s ) );
    strcat( s2, s );
    printf("%s\n",s2);
    return 0;
}  
[/PHP]The strcat functions will concatenate and ENTIRE character array.

yes, i know that, but as i already said that is not what i am trying to do 
thanks anyway

---

### Post by kartabosh on 2010-04-23
> **trent.josephsen said:**
> I don't know, and can't tell at the moment, what manpage Ubuntu has for strtok, but the one at [http://linux.die.net/man/3/strtok](http://linux.die.net/man/3/strtok) seems reasonably written and contains an example that you should be able to follow.
wow, that looks complicated and way out of my league

and speaking of books 
[http://ubuntuforums.org/showthread.php?p=9161272](http://ubuntuforums.org/showthread.php?p=9161272)

---

### Post by stchman on 2010-04-23
> **kartabosh said:**
> yes, i know that, but as i already said that is not what i am trying to do 
thanks anyway

My program and your correct program do EXACTLY the same thing.  It also might help if you tell us what you are trying to do.

---

### Post by kartabosh on 2010-04-23
> **stchman said:**
> My program and your correct program do EXACTLY the same thing.  It also might help if you tell us what you are trying to do.
in post #5 i said 
```
i dont want to copy a string i was just testing it, i want to copy certain letters from strings into other ones in random order 
i'm a beginner programmer as you may have already noticed so i just try to implement random stuff, now i'm trying to do the normal expression to rpn 
input: a+b-c
output: a b c - +
```
i know that your program does exactly what my program does now but i was trying to see how to individually add elements from a string to another one by one because i may want to skip exclamation marks, slash's, spaces and so on

---

### Post by lisati on 2010-04-23
Suggestion: forget using strcat in this context. Instead, work your way through the source string one character at a time, copying one character at a time, and only copying the characters you want.

Example:
```


....
   int i,j;
   char s1[20], s2[20];
....
   // initialise s1 here
...
   for (i=0,j=0; i<strlen(s1),j<sizeof[s2]-1; i++)
       if (s1[i]!='!')  // replace this test with whatever test suits
            s2[j++]=s1[i];
   s2[j]=0;
...

```

---

### Post by kartabosh on 2010-04-23
> **lisati said:**
> Suggestion: forget using strcat in this context. Instead, work your way through the source string one character at a time, copying one character at a time, and only copying the characters you want.

Example:
```


....
   int i,j;
   char s1[20], s2[20];
....
   // initialise s1 here
...
   for (i=0,j=0; i<strlen(s1),j<sizeof[s2]-1; i++)
       if (s1[i]!='!')  // replace this test with whatever test suits
            s2[j++]=s1[i];
   s2[j]=0;
...

```
thanks, i wanted to do that but some people told me its not really safe 
anyway whats with the two fors in one

---

### Post by lisati on 2010-04-23
> **kartabosh said:**
> thanks, i wanted to do that but some people told me its not really safe 
anyway whats with the two fors in one

It's only unsafe if you don't keep track of where your destination index/pointer is heading, hence the j<sizeof() bit. The i=0,j=0 bit could also have been written i=j=0.

---

### Post by kartabosh on 2010-04-23
> **lisati said:**
> It's only unsafe if you don't keep track of where your destination index/pointer is heading, hence the j<sizeof() bit. The i=0,j=0 bit could also have been written i=j=0.
yes i understand that but how does it work? it seams really strange to me to have more than 3 arguments in for

---

### Post by lisati on 2010-04-23
Perhaps someone better versed in "C" can explain it better than I can, but here goes:

In C, there are four parts to the "for" statement:
> for (init_exp; cond_exp; update_exp) loop_body_statement

Notice that each part in the parenthises "()" is separated by a semi-colon, not a comma.

What I had in my example was a multi-action init_exp (which takes care of what happens before the loop starts) and a mult-part cond_exp (which decides when the loop should end).

---

### Post by MadCow108 on 2010-04-23
your multi_part cond_exp will not work:
 i<strlen(s1),j<sizeof[s2]-1
the middle part must be a boolean expression
write it like that:
i<strlen(s1) && j<sizeof[s2]-1

also it might is better to move the strlen out of the for loop into a temporary variable so it doesn't get executed each loop iteration (the compiler can only do that by itself in very simple cases)

---

### Post by lisati on 2010-04-23
> **MadCow108 said:**
> your multi_part cond_exp will not work:
 i<strlen(s1),j<sizeof[s2]-1
the middle part must be a boolean expression
write it like that:
i<strlen(s1) && j<sizeof[s2]-1

also it might is better to move the strlen out of the for loop into a temporary variable so it doesn't get executed each loop iteration (the compiler can only do that by itself in very simple cases)

Thanks.

---

### Post by Compyx on 2010-04-23
You have a bug in your code, since the comma operator evaluates from left to right, discarding the value on the left. So the comma operator in the conditional part of the for-loop discards the result of 'i < strlen(s1)' and only uses the second condition (j<sizeof[s2]-1).

The use of the comma operator in the initialization part of a for-loop is fine since we only use the expressions for their side-effect (assigning values).

The conditional should be written as: ```

i < strlen(s1) **&&** j<sizeof[s2]-1;
```

As a side note, I would move the strlen() call out of the loop and declare i as a size_t, since that's what strlen() returns.

---

