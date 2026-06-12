---
title: "please explain the concept behind this problem"
date: 2011-08-27
forum: Programming Talk
---

### Post by Praveen30 on 2011-08-27
When i am running this code, nothing is printed on my terminal.i am using gcc compiler.can anyone explain me the concept behind it??i know this is related to signed and unsigned but i am not able to figure out..

[PHP]

#include<stdio.h> 
#define TOTAL_ELEMENTS (sizeof(array) / sizeof(array[0])) 
int array[] = {23,34,12,17,204,99,16};
  int main()
  {
      int d;
      for(d=-1;d <= (TOTAL_ELEMENTS-2);d++)
          printf("%d\n",array[d+1]);
      return 0;
 }

[/PHP]

---

### Post by OlyPerson on 2011-08-27
Have you tried any debugging?  For example, you could print out the value of TOTAL_ELEMENTS before the loop to make sure it's the value you want (although it should be, don't see anything wrong there).  Also, turn on -Wall in the compiler.

Also on a different note, you shouldn't use a for-loop in that way.  By that I mean you should probably just start d=0 and go until TOTAL_ELEMENTS - 1 instead of 2 as that's the 'usual' way and is less confusing.

```
#include<stdio.h> 
#define TOTAL_ELEMENTS (sizeof(array) / sizeof(array[0])) 
int array[] = {23,34,12,17,204,99,16};
  int main()
  {
      int d;
      for( d = 0; d <= (TOTAL_ELEMENTS-1); d++ )
          printf("%d\n",array[d]);
      return 0;
 }  
```

See how that's easier to read?

EDIT: Did you actually want an explanation of what the code is doing or why it's not working?

Code works for me when I do the changes I posted.

---

### Post by Senesence on 2011-08-27
@OlyPerson

Additional information won't hurt him. ;)

@Praveen30

A relatively simple google search brought me to these useful links:

[http://stackoverflow.com/questions/950051/confused-about-c-macro-expansion-and-integer-arithmetic](http://stackoverflow.com/questions/950051/confused-about-c-macro-expansion-and-integer-arithmetic)

[http://objectmix.com/c/208484-comparison-between-signed-unsigned-int.html](http://objectmix.com/c/208484-comparison-between-signed-unsigned-int.html)

I think that should clear up your confusion.

---

### Post by Bachstelze on 2011-08-27
Te result of sizeof is unsigned, so when you compare d and TOTAL_ELEMENTS-2, the value of d is not -1 but 4294967295 (2^32-1).

---

### Post by Praveen30 on 2011-08-27
> **Senesence said:**
> @OlyPerson

Additional information won't hurt him. ;)

@Praveen30

A relatively simple google search brought me to these useful links:

[http://stackoverflow.com/questions/950051/confused-about-c-macro-expansion-and-integer-arithmetic](http://stackoverflow.com/questions/950051/confused-about-c-macro-expansion-and-integer-arithmetic)

[http://objectmix.com/c/208484-comparison-between-signed-unsigned-int.html](http://objectmix.com/c/208484-comparison-between-signed-unsigned-int.html)

I think that should clear up your confusion.

thanks for info, that's what i want!!!

---

### Post by OlyPerson on 2011-08-27
> **Senesence said:**
> @OlyPerson

Additional information won't hurt him. ;)

@Praveen30

A relatively simple google search brought me to these useful links:

[http://stackoverflow.com/questions/950051/confused-about-c-macro-expansion-and-integer-arithmetic](http://stackoverflow.com/questions/950051/confused-about-c-macro-expansion-and-integer-arithmetic)

[http://objectmix.com/c/208484-comparison-between-signed-unsigned-int.html](http://objectmix.com/c/208484-comparison-between-signed-unsigned-int.html)

I think that should clear up your confusion.

Learn something new every day!  Still young, hope I can keep that up my whole life.

---

### Post by Arndt on 2011-08-27
> **Praveen30 said:**
> thanks for info, that's what i want!!!

You may want to ask gcc for warnings about this:

```
$ gcc -Wall -Wextra -c sign.c
sign.c: In function ‘main’:
sign.c:7: warning: comparison between signed and unsigned integer expressions

```

---

