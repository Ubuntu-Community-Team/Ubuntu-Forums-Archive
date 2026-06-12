---
title: "Help about C programming"
date: 2009-01-03
forum: Programming Talk
---

### Post by vietwow on 2009-01-03
Dear all, I am newbie aobut C, I'm reading book [http://beej.us/guide/bgc/output/html/singlepage/bgc.html](http://beej.us/guide/bgc/output/html/singlepage/bgc.html) and have some consfuse, need your help


First, when I need get a first element in a array, I need to declare a pointer for pointing to name of array without square brackets

For example :

```
int main()
{
char a[] = "Cats are better.";
char *p;

p = a;
printf("first element is : %c \n",*p);

```


And in the other way, I can declare a array with pointer :

```
int main()
{

char *array="hello world!";
char *parray, *first;

printf("first element : %c\n", *array);
printf("all : %s\n", array);

}

```

Both 2 codes are work well

From second code, I understand that code "**char *array="hello world!";**" will automatically create a array named array with content "hello world!" (so I could print all content with "array" variable in last line although I don't declare it before)

So now I use a new pointer for pointing to first element of variable "array" and print value of it but I got an "Segmentation fault". Detail is here :

```
#include<stdio.h>

int main()
{

char *array="hello world!";
char *parray, *first;

first=&array[0];

printf("first element : %c\n", *array);
printf("same : %s\n", *first);

}

```

run it :

```

[root@server ~]# ./taomang
first element : h
Segmentation fault

```

It can print *array but can't with *first 

Anybody can explain me about this ?

Thanks

---

### Post by prshah on 2009-01-03
> **vietwow said:**
> 
first=&array[0];


This is because you are trying to assign the address of the pointer array to first, not the address of the string ("Hello world") (which is pointed to by the address stored in array).

In essence you need to do ```

first=array
```

---

### Post by pmasiar on 2009-01-03
Check stickies, C is not considered best language for beginners. You may have easier start with Python, and when (after learning Python) you try C again, many things would make more sense.

---

### Post by vietwow on 2009-01-03
> **prshah said:**
> This is because you are trying to assign the address of the pointer array to first, not the address of the string ("Hello world") (which is pointed to by the address stored in array).

In essence you need to do ```

first=array
```

Dear prshah,

First, thanks for your reply

But as I told :

char *array="hello world!";

will automatically create a array named array with content "hello world!", so I think :
[B]
char *array="hello world!";[/B]

absolutely the same with :
**array[]="hello world!"**

And then I get address of fisrt element of this array[] :

first = &array[0]

And I think I can print *first which is derefence to first element of array[]

What's wrong with me ?

---

### Post by prshah on 2009-01-03
> **vietwow said:**
> 
And then I get address of fisrt element of this array[] :
first = &array[0]


OK I missed the part about [0]; this usage is correct. first will indeed hold the address of the first element of array.

Then I can't really figure out what's wrong here..

---

### Post by slavik on 2009-01-03
> **vietwow said:**
> Dear prshah,

First, thanks for your reply

But as I told :

char *array="hello world!";

will automatically create a array named array with content "hello world!", so I think :
[B]
char *array="hello world!";[/B]

absolutely the same with :
**array[]="hello world!"**

And then I get address of fisrt element of this array[] :

first = &array[0]

And I think I can print *first which is derefence to first element of array[]

What's wrong with me ?
you are incorrect. char *a is not the same as char a[];

also, a and &(a[0]) are the same, theyboth point tothe first element.

---

### Post by vietwow on 2009-01-03
> **slavik said:**
> you are incorrect. char *a is not the same as char a[];

also, a and &(a[0]) are the same, theyboth point tothe first element.

Can you explain what the differences between char *a and char []; are ? or give me the docs teach about this

Thanx

---

### Post by nvteighen on 2009-01-03
> **slavik said:**
> you are incorrect. char *a is not the same as char a[];

also, a and &(a[0]) are the same, theyboth point tothe first element.
Huh? *a != a[] ???

---

### Post by Cracauer on 2009-01-03
No, no, no.

All these language semantics play no role here and aren't the solution.

What you should have done is compile the program with warnings on, all warnings, and use -Werror.  That is an absolute must for a C beginner.

It would have told you right away what's wrong with the program:

```

% gcc -Wall -o ~/l ~/l2.c
/home/cracauer/l2.c: In function 'main':
/home/cracauer/l2.c:12: warning: format '%s' expects type 'char *', 
but argument 2 has type 'int'

```

  printf("same : %s\n", *first);
should have been
  printf("same : %s\n", first);

The compiler knows it, you just have to ask it.

Trust me, you'll get nowhere in C without full warnings and doing your best to solve, not just kill, each single one.

---

