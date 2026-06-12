---
title: "Very simple string manipulation in C"
date: 2008-11-22
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-22
I got this string:
```
[COLOR="DarkOrchid"]a/x(23.000000)y(58.000000)\n[/COLOR]
```
Then two variables:
```
**float** x;
**float** y;
```
How can I save 23.000000 to x and 58.000000 to y?

---

### Post by Sockerdrickan on 2008-11-22
This seems to work:
[php]#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
    char text[]="a/x(23.000000)y(58.000000)";

    printf("%s\n",text);

    strtok(text,"(");
    float x=atof(strtok(NULL,"("));
    float y=atof(strtok(NULL,"("));

    printf("x: %f y: %f\n",x,y);

    return 0;
}
[/php]I don't know if strtok can be used in a nicer way, someone please correct me if so.

---

### Post by cb951303 on 2008-11-22
> **Tux0r said:**
> This seems to work:
[php]#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
    char text[]="a/x(23.000000)y(58.000000)";

    printf("%s\n",text);

    strtok(text,"(");
    float x=atof(strtok(NULL,"("));
    float y=atof(strtok(NULL,"("));

    printf("x: %f y: %f\n",x,y);

    return 0;
}
[/php]I don't know if strtok can be used in a nicer way, someone please correct me if so.


correct me if I'm wrong but first strtok should give "23.000000)y". but you convert it to integer so atof function doesn't recognize last 2 char and gives you the correct answer
also second strtok will give "58.000000)", same prob...

EDIT: I guess that's a valid method. It's safe to use atof this way, sorry for confusion

---

### Post by cb951303 on 2008-11-22
> **crazyfuturamanoob said:**
> I got this string:
```
[COLOR="DarkOrchid"]a/x(23.000000)y(58.000000)\n[/COLOR]
```
Then two variables:
```
**float** x;
**float** y;
```
How can I save 23.000000 to x and 58.000000 to y?

if that format is consistent for all data then just read data starting from 4. to 12. and 16. to 24. It would also be faster...

---

### Post by crazyfuturamanoob on 2008-11-22
> **cb951303 said:**
> if that format is consistent for all data then just read data starting from 4. to 12. and 16. to 24. It would also be faster...

How to read data from a string then?

---

### Post by cb951303 on 2008-11-22
> **crazyfuturamanoob said:**
> How to read data from a string then?

[php]
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main()
{
    char x[10], y[10];
    float fx, fy;
    char text[]="a/x(23.000000)y(58.000000)";
       
    /* If you want to use them as strings */ 
    strncpy(x, text + 4, 9);
    strncpy(y, text + 16, 9);
    x[9] = '\0'; y[9] = '\0';
    printf("%s , %s\n", x, y);
    
    /* If you want to use them as float */
    fx = atof(x);
    fy = atof(y);
    printf("%f , %f\n", fx, fy); 
    
    return 0;
} [/php]

EDIT: Tux0r's method is valid too

---

### Post by Sockerdrickan on 2008-11-22
Not to mention if you know that the string style won't change:
[php]#include <stdio.h>

int main() {
    char text[]="a/x(23.000000)y(58.000000)";
    float x,y;

    sscanf(text,"a/x(%f)y(%f)",&x,&y);
    printf("x: %f y: %f\n",x,y);

    return 0;
}
[/php]

---

