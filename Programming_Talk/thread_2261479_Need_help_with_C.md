---
title: "Need help with C"
date: 2015-01-19
forum: Programming Talk
---

### Post by newbie13 on 2015-01-19
I am learning C language just for fun. Today I learned about if else loop and to test it I created a basic calculator. It had many bugs (first loop program that's why) which were cleared after googling and trying different things for about an hour. Now it works just like what I wanted. But there is one thing I didn't understand. The last editing which I had to do, was to add a dummy variable.
```
#include <stdio.h>
void main()
{
[COLOR=#ff0000]char opr, dummy;[/COLOR]
double n1, n2, ans;
printf("Enter first no:");
scanf("%lf", &n1);
printf("Choose operation(+,-,*,/):");
[COLOR=#ff0000]scanf("%c%c", &dummy, &opr);[/COLOR]
printf("Enter second no:");
scanf("%lf", &n2);
if (opr == '+')
{
ans = ((double)n1) + n2;
printf("\n%f + %f = %f", n1, n2, ans);
}
else if (opr == '-')
{
ans = ((double)n1) - n1;
printf("\n%f - %f = %f", n1, n2, ans);
}
else if (opr == '*')
{
ans = ((double)n1) * n2;
printf("\n%f * %f = %f", n1, n2, ans);
}
else if (opr == '/')
{
ans = ((double)n1) / n2;
printf("\n%f / %f = %f", n1, n2, ans);
}
else
{
printf("\nInvalid operation\n");
}
}
```

If I add that dummy variable then everything works properly. But, if I remove it, it skips the scanf for char and goes to the next line.

What am I doing wrong?

---

### Post by slickymaster on 2015-01-19
*Moved to the ***Programming Talk*** sub-forum*

---

### Post by schragge on 2015-01-19
See [thread=2258166]this thread[/thread]. As a quick and dirty hack you may try
```
scanf(" %c", &opr);
```

---

### Post by newbie13 on 2015-01-19
Worked! Thanks..

Link provided in the link provided is not working. But I got keywords to search from the link so the problem is solved.

Thank you..

---

