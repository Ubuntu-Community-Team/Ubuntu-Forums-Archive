---
title: "Unable to print string using a void pointer"
date: 2010-04-02
forum: Programming Talk
---

### Post by trilobite on 2010-04-02
Hi all -  

 In becoming familiar with void pointers in C, I've got the following code -  

```
 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h> 
#include <math.h> 
      
    
int main(void) 
{ 
  
  int a = 42; 
  char mystr[12] = "Just a test";   
  /*  Void pointer  */  
  void *mydata;      
              
  mydata = &a ; 
  printf("I am pointing at %d\n", *(int*) mydata);
 
  mydata = &mystr ; 
  printf("Now I am pointing at %c\n", *(char*) mydata);
 
  return 0; 

} 

``` 

However, this prints out the following - 
I am pointing at 42
Now I am pointing at J 

So, it is only printing the first character of the string, and if I try to use "%s", I get a segfault on the second printf. 

So, how do you print out a string using a void pointer? Is it even possible?  

Thanks in advance - 
- trilobite

---

### Post by lisati on 2010-04-02
I'm guessing that you are checking out the use of a void pointer prior to using it in a function. Wouldn't it be easier in a short program to use mystr directly when using %s?

---

### Post by dwhitney67 on 2010-04-02
> **trilobite said:**
> ...

So, it is only printing the first character of the string, and if I try to use "%s", I get a segfault on the second printf. 

I'm not sure what you attempted to get the seg-fault.  Had you tried the following, then everything would've worked fine:
```

printf("Now I am pointing at %s\n", (char*) mydata);

```



P.S.  Doing something like the following would generate a compiler warning (if -Wall is enabled); I just tested and found that this generates a segfault.  Get into the habit of using -Wall when compiling!
```

printf("Now I am pointing at %s\n", *(char*) mydata);

```

---

### Post by trilobite on 2010-04-02
> **dwhitney67 said:**
> I'm not sure what you attempted to get the seg-fault.  Had you tried the following, then everything would've worked fine:
```

printf("Now I am pointing at %s\n", (char*) mydata);

``` 

Great! Thanks very much for that, dwhitney67! 

You were spot-on - the segfault was indeed caused by my having an extra *  ( I had *(char*) instead of just (char*). ). 

@lisati - No. For now, I'm just getting used to the simplest use of void pointers (as shown). But yes, I'm aware that they can be used (for example) to make functions take generic arguments.  

Many thanks all....  :)  Bye for now - 
- trilobite

---

