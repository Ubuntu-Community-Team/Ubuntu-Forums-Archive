---
title: "How to break a line, and then go back up?"
date: 2012-04-05
forum: Programming Talk
---

### Post by rafaelcbf on 2012-04-05
[PHP]#include <stdio.h>
#include <iostream>
int A, B, a1, a2, a3, b1, b2, b3;
int main()
{
printf("Ingrece el valor de: a1=");
scanf("%i" ,&a1);
printf("Ingrece el valor de: a2=");
scanf("%i",&a2);
printf("Ingrece el valor de: a3=");
scanf("%i",&a3);
printf("Ingrece el valor de: b1=");
scanf("%i",&b1);
printf("Ingrece el valor de: b2=");
scanf("%i", &b2);
printf("Ingrece el valor de: b3=");
scanf("%i",&b3);
printf("A=<%i, %i, %i> Y B=<%i, %i, %i>\n\n", a1, a2, a3, b1, b2, b3);
printf("    |i j k|\nAxB=|%i %i %i|\n    |%i %i %i|\n\n", a1, a2, a3, b1, b2, b3);
printf("AxB=i|%i %i|\n     |%i %i|\r a");
}

[/PHP]

Ok so i'm makeing this program, but don't worry about the code, all I need help with is at he end the part that says [PHP]printf("AxB=i|%i %i|\n     |%i %i|\r a");[/PHP]

Again forget the code, It's still long from being done, what I need it to look like at the end is like this: 

[PHP]AxB=i|1 2|-j|1 2|+k|1 2|
     |1 2|  |1 2|  |1 2|[/PHP]


But, when I use "\n " it only lets me go down, so it ends up all looking "diagonal". What can I use to go up and down the lines. (Sorry If I don't make any scenes)

---

### Post by r-senior on 2012-04-05
I just ran it (entering 1 for every prompt) and got this:

```
$ ./test
Ingrece el valor de: a1=1
Ingrece el valor de: a2=1
Ingrece el valor de: a3=1
Ingrece el valor de: b1=1
Ingrece el valor de: b2=1
Ingrece el valor de: b3=1
A=<1, 1, 1> Y B=<1, 1, 1>

    |i j k|
AxB=|1 1 1|
    |1 1 1|

AxB=i|-2110525440 -1627702640|

```

Obviously you are missing arguments to the last printf (hence the random junk numbers), but I don't see diagonals.

---

### Post by rafaelcbf on 2012-04-05
Yeah I erased the last part, but yeah I guess you do need to see it, let me do it over, give me a few minutes.

---

### Post by rafaelcbf on 2012-04-05
[PHP]#include <stdio.h>
#include <iostream>
int A, B, a1, a2, a3, b1, b2, b3;
int main()
{
printf("Ingrece el valor de: a1=");
scanf("%i" ,&a1);
printf("Ingrece el valor de: a2=");
scanf("%i",&a2);
printf("Ingrece el valor de: a3=");
scanf("%i",&a3);
printf("Ingrece el valor de: b1=");
scanf("%i",&b1);
printf("Ingrece el valor de: b2=");
scanf("%i", &b2);
printf("Ingrece el valor de: b3=");
scanf("%i",&b3);
printf("A=<%i, %i, %i> Y B=<%i, %i, %i>\n\n", a1, a2, a3, b1, b2, b3);
printf("    |i j k|\nAxB=|%i %i %i|\n    |%i %i %i|\n\n", a1, a2, a3, b1, b2, b3);
printf("AxB=i|%i %i|\n     |%i %i|-j|%i %i|\n            |%i %i|+k|%i %i|\n                   |%i %i|", a2, a3, b2, b3, a1, a2, b1, b3, a1, a2, b1, b2);
}
[/PHP]

Ok so all the way at the bottom, what I want is for my numbers to be lined up horizontally, is it a little clearer now?

---

### Post by r-senior on 2012-04-05
Here's the output, for anybody trying to visualise what's going on:

```
$ ./test
Ingrece el valor de: a1=2
Ingrece el valor de: a2=3
Ingrece el valor de: a3=4
Ingrece el valor de: b1=5
Ingrece el valor de: b2=6
Ingrece el valor de: b3=7
AxB=i|3 4|
     |6 7|-j|2 3|
            |5 7|+k|2 3|
                   |5 6|
```

You can't go upwards with printf without using special terminal codes or a library like curses.

Why can't you rearrange your printf so that you do all the first line then all the second line?

```
[COLOR="Red"]AxB=i|1 2|-j|1 2|+k|1 2|[/COLOR]
[COLOR="Blue"]     |1 2|  |1 2|  |1 2| [/COLOR]
```

---

### Post by rafaelcbf on 2012-04-05
¬_¬ That actually makes a lot of sense... I got to learn to think outside the box, thanks a lot man.

---

