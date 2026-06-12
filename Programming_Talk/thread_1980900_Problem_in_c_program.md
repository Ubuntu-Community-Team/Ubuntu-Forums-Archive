---
title: "Problem in c program"
date: 2012-05-16
forum: Programming Talk
---

### Post by sreeharitk on 2012-05-16
hi all
Great day to you 
I amjust a beginner in C
and I made a program as below. 
The problem:   The program runs as below

enter first number
2
enter second number
4
enter operaend of program

Where It does not stop for entering 3rd input 'opera' if I give it as %d (int) it works!!
can anybody please help me with this!! 

```
#include <stdio.h>

main()
{
int num1,num2;
char opera;
printf ("enter first number \n");
scanf("%d",&num1);
printf ("enter second number \n");
scanf("%d",&num2);
printf ("enter opera");
scanf("%c",&opera);
printf ("end of program");
}
```

---

### Post by Some Penguin on 2012-05-16
The carriage return or newline is a character, too.

Check the manual page for how scanf handles spaces in the format string.  That should be helpful.

---

### Post by sreeharitk on 2012-05-16
Hey 
Thanks a lot for your help!!
I just found the solution.
its to just add a space in front of the '%c' in scanf line

scanf (" %c", &oper)

Thanks for your quick reply!!
Keep celebrating life :)

---

### Post by ivikas on 2012-05-16
put a leading space before %c,this will ignore space characters in input.

so your character reading  code should be 

```

scanf(" %c",&opera); // space before %c

```

---

### Post by Tony Flury on 2012-05-16
I would strongly suggest that this is a bad habit to get into.

Actually it is not normally recommended to used scanf on it's own to read user input from the terminal - exactly because of these end of line marker issues, and the high likely hood of user input errors. scanf can be used to read data from a file - where you can make assumptions about the format of each line.

Even if you are a beginner i would recommend that you start now with good habits in your programming style.

For user input from the terminal : look at using fgets to input an arbitary line of text from stdin, use a loop to strip away spaces, newlines etc at the start and end of the line and then use sscanf on the remainder to actually read your number (i.e. you use the power of scanf when you know you should have a number). Alternatively you could read the user input one character at a time, ignoring spaces, newlines etc  and adding the rest into a buffer for scanning with scanf.

Either method is preferable to the solution proposed here.

---

