---
title: "Any workaround to switch/case not supporting ranges?"
date: 2010-03-30
forum: Programming Talk
---

### Post by trilobite on 2010-03-30
Hi all - 

 As part of becoming more familiar with C, I'm wanting to do a simple "map" function which tests whether a value is in a given range and then returns a value. 

I've done the following code - 
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int map1(int inputval)
{  
   switch(inputval) 
     {
     case (0-9):         
        return 100;
        break; 
     case (10-19):                 
        return 200;
        break; 
     case (20-29):                 
        return 300;
        break; 
     case (30-39):                 
        return 400;
        break; 
     default: 
        return inputval; 
     }            
} 

    
int main(void) 
{ 
  
  char ch; 
  int inval; 
  int retval; 
            
  do { 
    puts("Enter a number :"); 
    scanf("%d", &inval);  
    
    retval = map1(inval);  
    
    printf("Your number maps to %d \n", retval);  
    
    printf("Try again? (y/n) : "); 
    scanf(" %c%*c", &ch);  
  } 
  
    while( toupper(ch) != 'N' );  
       
  return 0; 

} 


``` 

However, this gives me the error "Duplicate case value", and when I change it by putting 
(for example)  "case inputval >= 10 && inputval <= 19", I get "case label does not reduce to an integer constant".  

 So - does anyone know if there is a workaround for the case statement not supporting ranges? If so, what is it?  

Many thanks in advance - bye for now - 
- trilobite

---

### Post by dearingj on 2010-03-30
In this case, I think the best thing to do would be to divide inputval by 10 and store the result in a new temporary int, something like this:

```
int map1(int inputval)
{  
   int temp = floor( (double) inputval / 10); //Ensures that the value is always rounded down. I'm not sure if this actually necessary.
   switch(temp) 
     {
     case 0:        
        return 100;
        break; 
     case 1:                 
        return 200;
        break; 
     case 2:                 
        return 300;
        break; 
     case 3:                 
        return 400;
        break; 
     default: 
        return inputval; 
     }            
} 

```

---

### Post by trilobite on 2010-03-30
> **dearingj said:**
> In this case, I think the best thing to do would be to divide inputval by 10 and store the result in a new temporary int, something like this:

```
int map1(int inputval)
{  
   int temp = floor( (double) inputval / 10); //Ensures that the value is always rounded down. I'm not sure if this actually necessary.
   switch(temp) 
     {
     case 0:        
        return 100;
        break; 
     case 1:                 
        return 200;
        break; 
     case 2:                 
        return 300;
        break; 
     case 3:                 
        return 400;
        break; 
     default: 
        return inputval; 
     }            
} 

```

Hi dearingj!  

Thanks for that!  That looks like a good solution.  

(Sigh...) Yeah... I just wonder why it was that the designers of C decided not to support ranges in situations like this. 

 This would be *so* easy to do if C had an "in" keyword too (as Python does), and a "range" function. For example, C *should* be able to do something like this - 
```

 switch(myval)   
 { 
   case myval in range(0, 9): 
     /*  do something  */ 
     break; 
   case myval in range(10, 19):  
     /*  do something else */ 
     break; 
   case myval in range(20, 29):  
     /*  and yet something else  */ 
     break; 
    ....  
 }              

```  

That kind of approach just looks *so* obvious! 
Oh well... maybe in C1X....  ;)   
- trilobite

---

### Post by the_unforgiven on 2010-03-30
As an aside, you might find [Duff's device]("http://en.wikipedia.org/wiki/Duff%27s_device") interesting :).
It's an ingenious way to use switch-case :).

Though it's not related to question-at-hand, it's still very informative.

---

### Post by MadCow108 on 2010-03-30
gcc supports case ranges over the value ... value2 syntax:

[http://gcc.gnu.org/onlinedocs/gcc-3.3.1/gcc/Case-Ranges.html#Case%20Ranges](http://gcc.gnu.org/onlinedocs/gcc-3.3.1/gcc/Case-Ranges.html#Case%20Ranges)

but this is non-standard, so not very portable

---

### Post by SledgeHammer_999 on 2010-03-30
Or instead of switch/case use it's equivalent with if/else if. eg:

```

if (inputval >= 0 && inputval <= 9) return 100;
else if (inputval >= 10 && inputval <= 19) return 200;
else if (inputval >= 20 && inputval <= 29) return 300;
else if (inputval >= 30 && inputval <= 39) return 400;
else return inputval;
```

---

### Post by trilobite on 2010-03-31
Hi again all - 
 
 Thanks for those replies, the_unforgiven, MadCow108, SledgeHammer_999! Very useful!  

 Yeah - I think that the if/then/else approach looks cleanest in this case. I'll look at that "Duff's device" though - sounds interesting and I seem to remember hearing about it... :)   

 Thanks again all!  Bye for now - 
- trilobite

---

### Post by nvteighen on 2010-03-31
> **MadCow108 said:**
> gcc supports case ranges over the value ... value2 syntax:

[http://gcc.gnu.org/onlinedocs/gcc-3.3.1/gcc/Case-Ranges.html#Case%20Ranges](http://gcc.gnu.org/onlinedocs/gcc-3.3.1/gcc/Case-Ranges.html#Case%20Ranges)

but this is non-standard, so not very portable

Not only non-standard, but horrible... It introduces whitespace significance in a language that hasn't any!

---

### Post by Compyx on 2010-03-31
> **nvteighen said:**
> Not only non-standard, but horrible... It introduces whitespace significance in a language that hasn't any!

Well said.

And even more horribly, from that same page:
> 
This feature is especially useful for ranges of ASCII character codes:

     case 'A' ... 'Z':

That's what we have isalpha() and friends for, so we don't have to make assumptions about which encoding the system uses.



Whitespace is relevant in C though, take for example the expression:
```

a + ++b;

```
If you remove the whitespace from that expression, you get:
```

a+++b;

```
which, using C's maximum-munch strategy during parsing, translates to:
```

a++ + b;

```
which is not at all the same. So, in C, whitespace is irrelevant, except where it isn't. ;)

---

### Post by dwhitney67 on 2010-03-31
> **trilobite said:**
> Hi dearingj!  

Thanks for that!  That looks like a good solution.  

(Sigh...) Yeah... I just wonder why it was that the designers of C decided not to support ranges in situations like this. 

 This would be *so* easy to do if C had an "in" keyword too (as Python does), and a "range" function. For example, C *should* be able to do something like this - 

... 

That kind of approach just looks *so* obvious! 
Oh well... maybe in C1X....  ;)   
- trilobite

You could do something like this in C:
```

#include <stdio.h>
#include <stdlib.h>
#include <garter.h>


int main(int argc, char** argv)
{
   int value = atoi(argv[1]);

   consider_value
   {
      case_in_range(value, 0, 9)
          printf("Your input is between 0 and 9.\n");
          case_break

      case_in_range(value, 10, 19)
          printf("Your input is between 10 and 19.\n");
          case_break

      case_in_range(value, 20, 29)
          printf("Your input is between 20 and 29.\n");
          case_break

      case_default
          printf("Your input is greater than 29.\n");
          case_break
   }

   return 0;
}

```

Long before Python, there was C.


P.S.  You will need this for garter.h:
```

#ifndef GARTER_H
#define GARTER_H

#include <setjmp.h>

#define consider_value \
        jmp_buf __jbuf; \
        if (!setjmp(__jbuf))

#define case_break \
        longjmp(__jbuf, 1); }

#define case_in_range(v, l, h) \
        if ((v) >= (l) && (v) <= (h)) {

#define case_default \
        else {

#endif

```

---

### Post by Lux Perpetua on 2010-03-31
> **trilobite said:**
> (Sigh...) Yeah... I just wonder why it was that the designers of C decided not to support ranges in situations like this. Don't. C was never intended to be feature-rich. C is simple and transparent, but beyond that, you shouldn't expect it to do anything to make your life easier. > **Compyx said:**
> Whitespace is relevant in C though...In C (excluding preprocessor directives), any consecutive sequence of whitespace characters is equivalent to a single space. Often (but not always), even that space is redundant.

---

### Post by Compyx on 2010-03-31
> **Lux Perpetua said:**
> In C (excluding preprocessor directives), any consecutive sequence of whitespace characters is equivalent to a single space. Often (but not always), even that space is redundant.

That was what I was getting at, as my example demonstrated. You took my quote out of context.

---

