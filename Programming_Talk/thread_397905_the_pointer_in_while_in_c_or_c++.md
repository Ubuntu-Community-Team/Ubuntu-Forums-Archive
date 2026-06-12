---
title: "the pointer in while in c or c++"
date: 2007-03-31
forum: Programming Talk
---

### Post by LaoLiulaoliu on 2007-03-31
I think it is a simple question.But when I run it on my computer,I found it is a problem.The file stage2.c is a c file and the file stage2.cc is the same thing writing in c++.
///////////////////////////////////////////////////////////////////////////////////////
stage2.c
///////////////////////////////////////
#include <stdio.h>
int main()
{
	char *p1,*p2="computer";
	
	while((*p1=*p2)!='\0')
   	{
		
    	p1++;
//		printf("p1 is:%s,\n*p1 is:%c\n",p1,*p1);
		p2++;
//		printf("p2 is:%s,\n*p2 is:%c\n",p2,*p2);
	}
	printf("Now p1 is:%s\n*p1 is:%c\np2 is:%s\n*p2 is:%c\n",p1,*p1,p2,*p2);

	return 0;
}
/////////////////////////////////////////////
stage2.cc
//////////////////////////
#include <iostream>
int main()
{
	char *p1,*p2="computer";
	while((*p1=*p2)!='\0')
	{
		p1++;
		p2++;
	}
	std::cout<<p1<<std::endl<<*p1<<std::endl;
	std::cout<<p2<<std::endl<<*p2<<std::endl;
	return 0;
}

---

### Post by WW on 2007-03-31
p1 is a pointer, but it has not been initialized.  You need to assign p1 so that it points to a valid block of memory that can hold the copy of p2.  For example, before the 'while' statement,
```

p1 = (char *) malloc(strlen(p2)+1);

```
Also, since you increment p1 and p2 in the loop, at the end of the loop, they no longer point to the beginning of the strings.

Here is version of your program that does what I think you expected it to do:
```

/* stage2.c */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
    {
    char *p1,*p2="computer";
    char *q1,*q2;
    p1 = (char *) malloc(strlen(p2)+1);
    q1 = p1;
    q2 = p2;
    while((*q1=*q2)!='\0')
        {
        q1++;
        q2++;
        }
    printf("p1 is '%s'\n",p1);
    printf("p2 is '%s'\n",p2);

    return 0;
    }

```
(There are better ways to accomplish this, but I assumed you are writing this code to learn about pointers and related C/C++ language features.)

---

### Post by Wybiral on 2007-03-31
I assume the problem is that it's not printing anything at the end? That's because you are incrementing the pointers... After that loop, they will point to the space AFTER the string.

Try using temp pointers:
```

#include <stdio.h>
int main()
{
   char *p1,*p2="computer";

   char *temp1 = p1;
   char *temp2 = p2;

   while((*temp1=*temp2)!='\0')
   {

      temp1++;
      temp2++;
   }
   printf("Now p1 is:%s\n*p1 is:%c\np2 is:%s\n*p2 is:%c\n",p1,*p1,p2,*p2);

   return 0;
}

```

Now you need to think about that is wrong with this...

We know that p2 points to "computer" in memory... What about p1? You're playing a dangerous game by write into memory that you haven't allocated. Try something like this...

```

#include <stdio.h>
int main()
{
   char p1[9],*p2="computer";

   char *temp1 = p1;
   char *temp2 = p2;

   while((*temp1=*temp2)!='\0')
   {

      temp1++;
      temp2++;
   }
   printf("Now p1 is:%s\n*p1 is:%c\np2 is:%s\n*p2 is:%c\n",p1,*p1,p2,*p2);

   return 0;
}

```

Now you know that p1 has 9 free bytes to copy "computer\0" into.

Pointers are really handy, but be careful with them. You can easily crash a program writing to unclaimed memory like that.


EDIT:

lol, WW beat me to it.

---

### Post by rplantz on 2007-03-31
I will make a style remark here. Both WW and Wybiral's programs are excellent. But I (as a teacher) have seen students labor many hours trying to debug a loop because they do not use parentheses to enforce correct precedence in a while loop conditional. I always recommended that they get in the habit of avoiding side effects in the conditional statement.

That is,
```

   while((*temp1=*temp2)!='\0')

```
correctly copies the byte that temp2 is pointing to into where temp1 is pointing to. This is the "side effect" of the conditional statement. It **then** tests to see if that byte was not '\0'.

If you forget the parentheses around the assignment statement, the != operator has precedence and the terminating null character ('\0') will not be copied. Even worse, there is a good chance that the memory you are copying to has a zero there most of the time. So you will not see this bug during your exhaustive testing. Ship it to the user, and it appears right away. (Naive users simply do not behave the way we want them to. :))

So I recommend to my students that they do something like:
```

   *temp1 = *temp2;
   while(*temp1 != '\0')
   {
      temp1++;
      temp2++;
      *temp1 = *temp2;
   }

```
This is very slightly less efficient, but the extra operations are performed **outside** the loop. So the performance hit is negligible. By the way, when I compiled both versions with -O2 optimization, the resulting code was identical.

Again, I want to emphasize that this is a matter of style and is intended to help avoid silly errors. (Silly errors are usually more difficult to debug. :))

---

### Post by slavik on 2007-03-31
As a student, I have to agree. side effects in loops are 'not good' ... even though K&R do it in the C book :(

---

### Post by Wybiral on 2007-03-31
Personally, unless I had to, I wouldn't even use my own memory copying routines. I also wouldn't use strcpy or strncpy because they handle the NULL terminator funny. But memcpy is a pretty good alternative.

```

#include <stdio.h>
#include <string.h>

int main()
{
   char p1[9], *p2="computer";
   memcpy(p1, p2, strlen(p2)+1);
   printf("Now p1 is:%s\n*p1 is:%c\np2 is:%s\n*p2 is:%c\n", p1, *p1, p2, *p2);
   return 0;
}

```

You could also use something like rplantz suggested, but with a for loop instead...

```

#include <stdio.h>
int main()
{
   char p1[9],*p2="computer";

   char *temp1 = p1;
   char *temp2 = p2;

   for(*temp1=*temp2; *temp1 != '\0'; *temp1=*temp2)
   {
      temp1++;
      temp2++;
   }
   printf("Now p1 is:%s\n*p1 is:%c\np2 is:%s\n*p2 is:%c\n",p1,*p1,p2,*p2);
   return 0;
}

```

---

### Post by slavik on 2007-03-31
how about this version?

```

#include <stdio.h>
int main()
{
   char p1[9],*p2="computer";

   char *temp1 = p1;
   char *temp2 = p2;
   int i;
   for(i=0; temp2[i] != '\0'; i++)
   {
      temp1[i] = temp2[i];
   }
   printf("Now p1 is:%s\n*p1 is:%c\np2 is:%s\n*p2 is:%c\n",p1,*p1,p2,*p2);
   return 0;
}

```

---

### Post by rplantz on 2007-03-31
> **slavik said:**
> how about this version?

```

#include <stdio.h>
int main()
{
   char p1[9],*p2="computer";

   char *temp1 = p1;
   char *temp2 = p2;
   int i;
   for(i=0; temp2[i] != '\0'; i++)
   {
      temp1[i] = temp2[i];
   }
   printf("Now p1 is:%s\n*p1 is:%c\np2 is:%s\n*p2 is:%c\n",p1,*p1,p2,*p2);
   return 0;
}

```

The problem with this one is it does not copy the string terminator ('\0'). I think the OP wanted to use or learn more about pointers. Here's another way, using pointers:
```

#include <stdio.h>
int main()
{
   char p1[9],*p2="computer";

   char *temp1 = p1;
   char *temp2 = p2;
   int i;
   for(i=0; *(temp2+i) != '\0'; i++)
   {
      *(temp1+i) = *(temp2+1);
   }
   *(temp+i) = '\0';
   printf("Now p1 is:%s\n*p1 is:%c\np2 is:%s\n*p2 is:%c\n",p1,*p1,p2,*p2);
   return 0;
}

```
Notice that I've added the NULL character. This also has a gotcha -- if you're using C++ and do for (int i = 0; *(temp2*i) != '\0'; i++) I think that the value of i will be undefined after you leave the for loop. I don't know offhand what the standard says, but I would not trust a compiler to do the "right" thing.

For newer programmers, not all versions of all compilers necessarily adhere to the standards. Sometimes they "exceed" the standards, which can lure you into writing non-portable code. And sometimes they simply do the wrong thing.

By the way, I'm pretty sure that I've have seen compilers treat pointer notation differently from array notation in the assembly language they generate. (Another reason for learning how to read assembly language.)

---

### Post by Wybiral on 2007-03-31
> **rplantz said:**
> By the way, I'm pretty sure that I've have seen compilers treat pointer notation differently from array notation in the assembly language they generate. (Another reason for learning how to read assembly language.)

I couldn't agree more! Any good C programmer should at least have a base level understanding of assembly.

After all... C is translated to assembly before it becomes an executable. So understanding more about that middle step will probably be the most enlightening experience for any C programmer and will allow you to improve and understand your code a lot.

---

### Post by wj32 on 2007-03-31
Wait... so you're trying to do a strcpy?

#include <stdio.h>

int main(int argc, char *argv[])
{
    char dest[9];
    char *src = "computer";
    int i = 9;
    
    while (i--)
        dest[i] = src[i];
    
    printf("%s", dest);
}

---

