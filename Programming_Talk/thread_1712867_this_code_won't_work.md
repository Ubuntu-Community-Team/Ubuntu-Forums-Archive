---
title: "this code won't work"
date: 2011-03-23
forum: Programming Talk
---

### Post by med linux on 2011-03-23
[CENTER][SIZE=3][COLOR=Red]good morning ;[/COLOR][/SIZE]
[SIZE=3][COLOR=Red]this programme is created to find x^y [/COLOR][/SIZE]
[SIZE=3][COLOR=Red]but it show every time an random number !!! [/COLOR][/SIZE]
[SIZE=3][COLOR=Red]could you help me please [/COLOR][/SIZE]
[SIZE=3][COLOR=Red]and thank you so much .... [/COLOR][/SIZE]
[/CENTER]
```

#include <stdio.h>
int nbpos (int x)
{
    int c,cpt ;
    do
    {
        x=x/10;
        c++;
    }
    while (x!=0);

    return c;
}


int puiss (int x , int y)
{
    int i=1,s=1;
printf ("\n--- x == %d --- s == %d---- y == %d\n",x,s,y);    
/*
for (i=1;i<y;i++)
    {
        s=s+1;
        
    }
*/
return s;
}

main()
{
int x=10,y,e;

    scanf("%d",&y);
    printf (" %d  ********** \n",nbpos(y));


e=nbpos(y);
e=puiss (x,e);
printf("////// %d \n",e);
}

```

---

### Post by Zugzwang on 2011-03-23
You do not initialise all variables in nbpos, in particular not the variable "c". Compile the program with the "-Wall" parameter to the compiler to see more warnings you should consider to fix.

---

### Post by med linux on 2011-03-23
ok ...
but the problem is in the second function !

---

### Post by Zugzwang on 2011-03-23
> **med linux said:**
> ok ...
but the problem is in the second function !

Your "second function" isn't doing anything except for printing something out and returning 1. What do you expect it to do?

---

### Post by Tony Flury on 2011-03-23
Also I hope that there is some code missing as i don't think your code gets anywhere close to doing what you want.

For instance the puiss function (if you remove the comments around your for loop) will completely ignore the value of x - whatever that is - and will only return y-1, but a very expensive way of doing it - as it stands - with the for loop commented out - it will only ever return 1

If you add some comments to your code maybe we might be able to help,

I assume there is a good reason why you wont do pow(x,y) - i.e. an optimised library function to do exactly what you want.

---

### Post by med linux on 2011-03-23
mmm ok 

thank you 

but I want to ask you about some thing 
this is the result
```

15
 2  ********** 

--- x == 10 --- s == 1---- y == 14409718
////// 14409718 


```

as you see 
printf do its work verry well 

but when send its value ( of  nbpos(y) ) in the fonction puiss 

he prints a random integer !

---

### Post by Zugzwang on 2011-03-23
> **med linux said:**
> 
but when send its value ( of  nbpos(y) ) in the fonction puiss 

he prints a random integer !

This is because you did not initialize "c" in the first function. In your main-program you first call "nbpos(y)" and store the result into "e". As in "nopos", you increment an uninitialized value until you have done something and return this value, this makes "e" essentially an uninitialized and thus random value. Note that it is not truly random, but rather only non-deterministic. The variable "e" is then used as parameter to your second function, where the value is finally printed out.

---

### Post by Tony Flury on 2011-03-23
you need to repost your code with corrections.

---

### Post by Pithikos on 2011-03-23
What I don't understand is why you use different names for the variables:
> **med linux said:**
> ```

int nbpos (int x)
printf (" %d  ********** \n",nbpos(y));

```
 
That makes the code really hard to follow. First y is something else then it becomes x then suddenly it becomes y again etc. If these are just some arbitrary numbers you can name the variables something like n1, n2 instead. Much easier to read.

---

