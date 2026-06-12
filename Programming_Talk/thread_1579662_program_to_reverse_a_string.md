---
title: "program to reverse a string"
date: 2010-09-22
forum: Programming Talk
---

### Post by jamesbon on 2010-09-22
I am writing a program to reverse a string which should not use any standard 
c library functions like sizeof,strlen 
the following program is giving me Segmentation fault when ever I am compiling it.

```

#include<stdio.h>
int main ()
{
int i,j;
char *p,*s;
 p="abcdefgh";
 i=0;j=0;
 s=p;
        while (p[i] != '\0')
        {
        printf("%d  %c\n ",i,p[i]);
        i++;
        }
        i--;

       while (i>=0){
         s[j]=p[i];
         j++;
        i--;
        printf("\n j=%d i=%d",j,i);
        }
  printf(" %s\n",s);
}

```

I used gdb and found 
```

         **s[j]=p[i];**

```
is the line giving problem.
Can some one point me to what can be the reason for segmentation fault?

---

### Post by Zugzwang on 2010-09-22
Try to compile your program using "g++" instead of "gcc" for a test. You will get one warning:
```

test.c: In function &#8216;int main()&#8217;:
test.c:6: warning: deprecated conversion from string constant to &#8216;char*&#8217;

```

I've read in my C++ book that good C programs should compile fine with a C++ compiler as well as the latter is more strict with some issues. While probably this advise is a little bit outdated, in your particular case it is not a bad one, as the warning you obtain really tells you something about your problem.

Google up what the warning is supposed to mean, why the conversion is deprecated and then think how that relates to your program.

---

### Post by Zugzwang on 2010-09-22
Oh, my first double post - wonder why that happened.

---

### Post by r-senior on 2010-09-22
I think you need to initialise your string like this:

```

char *s, p[]="abcdefgh";

```

There is a subtle difference between declaring a pointer to a string literal and initialising a character array with one. 

(Your algorithm is broken by the way, the assignments will crash in the middle of the string and you'll end up with "hgfeefgh").

---

### Post by Bachstelze on 2010-09-22
Just to nitpick, sizeof is an operator, not a function.

---

### Post by schauerlich on 2010-09-22
Hint: You only need to iterate halfway through the string, but you can affect two characters at a time.

---

### Post by tbastian on 2010-09-22
> **jamesbon said:**
> 

```

 s=p;

       while (i>=0){
         s[j]=p[i];
         j++;
        i--;
        printf("\n j=%d i=%d",j,i);
        }


```


Someone mentioned your error with the initialisation of p, but you're also making a similar error with s. You're declaring a pointer to a char with s, then making it point to the same thing p is pointing to. When you're 'reversing' your string, you're really reversing the second half, and clobbering the first half. The string 'abcdef' will end  up being 'feddef'. to fix this try this:

```

#include<stdio.h>

int main ()
{
   int i = 0,j = 0;
   char *s;
   char * p= "abcdefgh";

   while ( p[i] != '\0' )
   {
        printf("%d %c\n",i,p[i]);
        i++;
   }

   i--;

   s = (char *) malloc ( i );

   while ( i >= 0 ) {
       s[j]=p[i];
       j++;
       i--;
       printf("\n j=%d i=%d",j,i);
   }

   printf(" %s\n",s);
   free ( s );
   return 0;
}

```

---

### Post by worksofcraft on 2010-09-23
I know some people won't believe this, but reversing strings properly is actually a very important function.

You see, some languages like Arabic write from right to left and others like English write left to right and when you try to mix them, or translate them, then reversing strings is really useful.

The most difficult bit is reversing strings that have multi-byte characters in them... like utf-8, so I hope they give you a real challenge for your next assignment because I think this one was too easy ;)

---

### Post by dwhitney67 on 2010-09-23
> **worksofcraft said:**
> I know some people won't believe this, but reversing strings properly is actually a very important function.

I for one am a non-believer because it has not been required in the 20+ years I have been working as a s/w engineer.

> **worksofcraft said:**
> 
You see, some languages like Arabic write from right to left and others like English write left to right and when you try to mix them, or translate them, then reversing strings is really useful.

This has no relevance.  One cannot map Arabic directly to Western text, no more than one could map Thai text to Western text.  One can translate, but there is not, or may not be, a one-for-one correspondence of each letter of the respective alphabets.

> **worksofcraft said:**
> 
The most difficult bit is reversing strings that have multi-byte characters in them... like utf-8, so I hope they give you a real challenge for your next assignment because I think this one was too easy ;)
Each multi-byte character should be treated as a single unit.  Thus the algorithm for reversing the units should be no different than that of reversing single-byte characters.

---

### Post by r-senior on 2010-09-23
It does, however, make a convenient programming assignment to teach pointer and array manipulation. Especially if you impose the restriction that standard library functions cannot be used.

---

### Post by jamesbon on 2010-09-23
> **r-senior said:**
> 

```

char *s, p[]="abcdefgh";

```

There is a subtle difference between declaring a pointer to a string literal and initialising a character array with one. 

Can you give me some link to understand what you said above I am not clear with what to read or search.

---

### Post by dwhitney67 on 2010-09-23
In the following line of code, a _pointer_ is being initialized to point to a constant character string (ie one that cannot be modified).
```

char* text = "This is some text.";

```

In the code below, an _array_ is being initialized (populated with chars).  This is different from initializing a pointer (as shown above), even though the string literal ("This is some text") in either case is a constant character string.
```

char text[] = "This is some text.";

```

---

### Post by worksofcraft on 2010-09-23
> **dwhitney67 said:**
> I for one am a non-believer because it has not been required in the 20+ years I have been working as a s/w engineer.


I used it for formatting numbers as text... this is quite important when you don't have a standard library to do it for you, so from that point of view this assignment is quite realistic, but I discovered it malfunctions when you use Chinese digits that take more than one byte of utf-8

> 
This has no relevance.  One cannot map Arabic directly to Western text, no more than one could map Thai text to Western text.  One can translate, but there is not, or may not be, a one-for-one correspondence of each letter of the respective alphabets.


So for my program that says: printf("The Arabic word for \"Yes\" is \"%s\"\n", ArabicYes); it be irrelevant if it says &#1592;. &#1606;&#1593;&#1605;, &#1571;&#1580;&#1604;, &#1576;&#1604;&#1609; or has it reversed and it wouldn't matter if the utf=8 bytes are all back to front too?

p.s. Meh... I suppose my real point is that I'm wondering if we should be doing student
's assignments for them, or should tell them they need the practice themselves ;)

---

### Post by r-senior on 2010-09-24
> **worksofcraft said:**
> I suppose my real point is that I'm wondering if we should be doing student's assignments for them, or should tell them they need the practice themselves ;)
We shouldn't, but using web resources and asking for advice is part of programming these days. As long as whoever is doing the assignment learns something by coming on here and doesn't just walk away with a complete solution to copy & paste, that's fine by me.

There is a policy on not doing homework on the forum:

[quote=Ubuntu Forums Code of Conduct]While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.[/quote]

I suspect misunderstanding and fear of having the thread closed encourages some students to create misleading posts to disguise their real purpose. I'd rather people were honest. Suppose someone posted, "I've been given a homework assignment to [insert problem with tenuous practical use here] but I'm stuck. Here's what I have written so far. Where am I going wrong?". 

I think people would be quite happy to help with that (and the thread should not be closed based on the policy I've quoted). Knowing it's an assignment people are more likely to give suggestions and hold back on churning out complete solutions that could be plagiarised.

---

### Post by dwhitney67 on 2010-09-24
> **r-senior said:**
> ... I'd rather people were honest. Suppose someone posted, "I've been given a homework assignment to [insert problem with tenuous practical use here] but I'm stuck. Here's what I have written so far. Where am I going wrong?". 

I think people would be quite happy to help with that (and the thread should not be closed based on the policy I've quoted). Knowing it's an assignment people are more likely to give suggestions and hold back on churning out complete solutions that could be plagiarised.

I agree to a certain extent.  In the scenario you presented, I do not see any problem helping this individual on a one-on-one basis; however any replies to assist the student can, and probably will be, seen by other students, who will never have to even lift a finger before obtaining a partial or critical hint at solving the problem.

Since policing who has access to the threads in which homework problems are discussed is impossible, it is best practice to close down these threads.

And as for this thread, it should be closed down.  We know this thread is about homework, and by now, I have hopefully made the point that any assistance offered here may unjustly help next year's students.

---

### Post by ibuclaw on 2010-09-24
> **r-senior said:**
> There is a policy on not doing homework on the forum:
I would prefer it if you didn't wave the CoC around. Besides there's a difference between 'teaching' and 'giving away' the answer (hint: one helps the student figure out the solution for himself).

If one just asks for the code (ie: How to reverse string in C?) that is a homework violation IMO. That is not the case here.

> **jamesbon said:**
> I am writing a program to reverse a string which should not use any standard 
c library functions like sizeof,strlen 
the following program is giving me Segmentation fault when ever I am compiling it.

...

**Can some one point me to what can be the reason for segmentation fault?**

Now, can you continue on topic of the thread? :-)

---

### Post by sudipm on 2010-09-24
> **jamesbon said:**
> I am writing a program to reverse a string which should not use any standard 
c library functions like sizeof,strlen 
the following program is giving me Segmentation fault when ever I am compiling it.
 
```

#include<stdio.h>
int main ()
{
int i,j;
char *p,*s;
 p="abcdefgh";
 i=0;j=0;
 s=p;
        while (p[i] != '\0')
        {
        printf("%d  %c\n ",i,p[i]);
        i++;
        }
        i--;
 
       while (i>=0){
         s[j]=p[i];
         j++;
        i--;
        printf("\n j=%d i=%d",j,i);
        }
  printf(" %s\n",s);
}

```
 
I used gdb and found 
```

         **s[j]=p[i];**

```
is the line giving problem.
Can some one point me to what can be the reason for segmentation fault?
 
segmentation fault is there because you are not terminating the string s. make it like this 
```

#include<stdio.h>
int main ()
{
int i,j;
char *p,*s;
 p="abcdefgh";
 i=0;j=0;
 s=p;
        while (p[i] != '\0')
        {
        printf("%d  %c\n ",i,p[i]);
        i++;
        }
        s[i]='\0';
 
        i--;
 
       while (i>=0){
         s[j]=p[i];
         j++;
        i--;
        printf("\n j=%d i=%d",j,i);
        }
  printf(" %s\n",s);
}

```
this will solve your segmentation fault problem.. and about reversing , try to implement that yourself

---

### Post by r-senior on 2010-09-24
> **ibuclaw said:**
> I would prefer it if you didn't wave the CoC around.
I quoted from the CoC to illustrate that it does not preclude asking for hints but discourages asking for solutions. 

Apart from being off-topic, why is that not acceptable? :confused:

---

### Post by dwhitney67 on 2010-09-24
> **ibuclaw said:**
> I would prefer it if you didn't wave the CoC around. Besides there's a difference between 'teaching' and 'giving away' the answer (hint: one helps the student figure out the solution for himself).

If one just asks for the code (ie: How to reverse string in C?) that is a homework violation IMO. That is not the case here.



Now, can you continue on topic of the thread? :-)

Yes it is the case here!  It is a HOMEWORK problem. Regardless of the travesties that the student may be suffering due to their ineptness at solving the problem, it is between them and their instructor.

You have to think beyond the scope of this one moment in history.  Every thing committed to this thread will be available "forever"; the next student will pretty much have the solution laid out in front of them.  Who's to say the OP will not post the final solution himself??

---

### Post by jamesbon on 2010-09-25
Let us hold on this thread for a while those of you are giving me some lecture about CoC 
can you solve any of my doubts here
[http://ubuntuforums.org/showthread.php?t=1575088](http://ubuntuforums.org/showthread.php?t=1575088)
if not then keep your mouth shut.

---

### Post by jamesbon on 2011-03-28
> **sudipm said:**
> segmentation fault is there because you are not terminating the string s. make it like this 
        s[i]='\0';
this will solve your segmentation fault problem.. and about reversing , try to implement that yourself
So why does terminating s with null character  work.To clear that this is not a home work problem and I am just brushing up my concepts the original problem was asked 7 months ago and now also I am continuing in the same thread.

---

### Post by Some Penguin on 2011-03-28
Because that's the C convention.  Most function that receive a (char*) meant to be interpreted as a string do not receive the length of the string, and there is no other convention for obtaining the length.  That means they have to look for *something* to know when to stop and in C, that's the null byte.

Languages have been designed in other ways, but allowing direct pointer access gives you very few alternatives.  For instance, it's entirely legal to pass a pointer to the *middle* of a string, so the Pascal convention of shoving length metadata in the beginning simply wouldn't work.

---

