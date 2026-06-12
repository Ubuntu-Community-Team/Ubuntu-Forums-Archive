---
title: "need help with a small C program."
date: 2010-07-01
forum: Programming Talk
---

### Post by Cammaaron on 2010-07-01
I am learning C out fom the C for dummies.

```

source code: 
#include <stdio.h>
#include <stdlib.h>

int main()
{
char a,b;
printf("which character is greater? \n");
printf("type a single character: ");
a=getchar();
printf("type a second character: ");
b=getchar();
if (a > b)
{
printf("%c",a);
}
else if(b > a)
{
printf("%c",b);
}
else
{
printf("twice");
}
return(0);
}

```

It causes this to happen
```

type a single character: a
type a second character: aaaron@aaron-laptop:~$ c
[/CODE[
same happens if I include fflush after the "a=getchar()"

If I used fpurge instead of fflush it gives this:
[CODE]
greater.c:(.text+0x34): undefined reference to `fpurge'
collect2: ld returned 1 exit status

```

---

### Post by dwhitney67 on 2010-07-01
Your program needs to account for the newline character (inserted into the stdin stream when you press the <return> key).  Thus for now, so as not to dwell too much on the issue, just insert two getchar() statements back-to-back.  One will read the character you enter, the other will read the newline.

---

### Post by Cammaaron on 2010-07-01
The problem is that it is not letting me type in the second character.

---

### Post by dwhitney67 on 2010-07-01
> **Cammaaron said:**
> The problem is that it is not letting me type in the second character.

Works for me...

```

#include <stdio.h>

int main(void)
{
   int a, b;

   printf("Enter a character: ");
   a = getchar();
   getchar();

   printf("Enter another character: ");
   b = getchar();
   getchar();

   printf("You entered %c and %c\n", a, b);

   return 0;
}

```

Another approach, so hopefully you will fully understand what is going on:
```

#include <stdio.h>

int main(void)
{
   int a, b, nl;

   printf("Enter a character: ");
   a = getchar();
   while ((nl = getchar()) != '\n');   // flush stdin until a newline char is found

   printf("Enter another character: ");
   b = getchar();
   while ((nl = getchar()) != '\n');

   printf("You entered %c and %c\n", a, b);

   return 0;
}

```

---

### Post by Cammaaron on 2010-07-01
ok, I found out why it didn't work.

The gcc didn't support the function I was trying to call.

I found a forum that actually had the author comments that it was a mistake to use the fpurge command, and to use something else. Which basically the almost the same thing that [dwhitney67]("http://ubuntuforums.org/member.php?u=322753") wrote on the second code block.

---

