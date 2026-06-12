---
title: "C - Passing a bidimensional array to a function"
date: 2006-01-17
forum: Programming Talk
---

### Post by sourc3 on 2006-01-17
Hi, as a newbie in C programming, I've got this problem. I need to pass a 3x3 bidimensional array to a function, but I don't know how to do it. Here's my code:
```

#include <stdio.h>

void pass(int *);
int array[3][3] = {0};
int *aPTR = &array[0][0];
main() {
printf("Start.\n");
pass(*aPTR);
printf("Finish\n");
return;
}

void pass(int *a) {
printf("Array[2][1] is %d.\n", *a);
return;
}
```

Would you please help me understand my mistakes and maybe suggest some good readings? Thanks in advance! ;)

---

### Post by Alpha_toxic on 2006-01-17
Well, as I recall, you'r array is actually not array of ints, but array of pointers to arrays of ints, so you should be passing not [COLOR="Red"]int*[/COLOR], but [COLOR="#ff0000"]int**[/COLOR] (but I'm not sure for the exact syntax). I think that even this [COLOR="Red"]aPTR[/COLOR] should be [COLOR="#ff0000"]int **aPTR[/COLOR].

As for good books, try sth from Donald Knuth, like "The art of computer programing" (a very good book for algorithms, but not for C syntax)

---

### Post by thumper on 2006-01-17
When passing aPTR to method *pass* you don't want to dereference it.

---

### Post by tbrownaw on 2006-01-17
Mistakes:
@ aPTR has type int*, *aPTR has type int, pass() takes an argument of type int*.
@ What gets printed is array[0][0], not array[2][1]. (the output is inaccurate)

Notes:
@ To pass an actual bidimensional array, you need to know the size at compile time. It looks like "pass(int a[3][3])".
@ In C, pointers and arrays are similar and somewhat interchangeable: *aPTR == array[0][0], *(aPTR+3) == array[1][0], *(aPTR+4) == array[1][1].
@ A multidimensional array is stored in memory exactly like a one-dimensional array with the same number of cells. What alpha_toxic said isn't correct here.
@ **array has type int, *array has type int*, but array does not have type int**. array also does not have type int*. array and *array have the same value, which is also the same as &array[0][0] and &array.

Tim

---

### Post by rock freak on 2006-01-17
hey there,

have you used and passed local varibles yet as i see you are currently using globals!

as for reading in go with Practical C by o'reily ive nearly finished it now and it has been a very good read!

ill get back to you one the code

---

### Post by sourc3 on 2006-01-17
Thanks for the replies, i really appreciate. I've corrected the code. Now it's like this:
```

#include <stdio.h>

void pass(int *);

main() {

int array[3][3] = {0,0,0,0,0,0,0,3,1};
int *aPTR = &array[2][1];
printf("Start.\n");
pass(aPTR);
printf("Finish\n");
return;
}

void pass(int *a) {
printf("Array[2][1] is %d.\n", *a);
return;
}

```

Well, it works, but I feel I did not understand well all the suggestion you gave me. Maybe I need to study pointers a little bit more. Thanks! ;)

---

### Post by skirkpatrick on 2006-01-17
> **sourc3]Thanks for the replies, i really appreciate. I've corrected the code. Now it's like this:
```

#include <stdio.h>

void pass(int *) said:**
> [3] = {0,0,0,0,0,0,0,3,1};
int *aPTR = &array[2][1];
printf("Start.\n");
pass(aPTR);
printf("Finish\n");
return;
}

void pass(int *a) {
printf("Array[2][1] is %d.\n", *a);
return;
}

```

Well, it works, but I feel I did not understand well all the suggestion you gave me. Maybe I need to study pointers a little bit more. Thanks! ;)

You can get rid of aPTR completely as well.  Here are a couple of ways to call pass():

1) pass (&array[2][1]);

2)
int i, j;
for (i = 0; i < 3; i++)
{
   for (j = 0; j < 3; j++)
   {
      pass (&array[i][j]);
   }
}


When you defined pass(), you specified that it's parameter is a pointer to an integer.  The '&' symbol means "address of" so &array[2][1] means "the address of the integer at offset 2,1" which is a pointer to an integer.

Hope this helps.

---

### Post by sourc3 on 2006-01-17
Thanks, I was just thinking of that!

---

### Post by rock freak on 2006-01-17
pointers are great yet they can be annoying as well, you will probably find that out!!!!

---

### Post by skirkpatrick on 2006-01-17
And for God's sake, make sure every function tests to see if a pointer is null, or zero, before using it.  That and running off the end of an array are the biggest reasons for programs crashing.  Back in the DOS days, that would get you a screen full of smilie faces and odd characters :)

---

### Post by purpleturtle on 2006-02-02
I tend not to overdo parameter checking in the

int my_func(char *param)
{
  if (param == NULL)
    return 0;
  :
  :
}

sense, but what I do like to do is to put assertions in to make sure that these situations are spotted immediately during development:

int my_func(char *param)
{
  assert(param != NULL);
  :
  :
}

And then the release version of the program runs nice and fast.. :-)  Just don't misuse asserts for stuff that really should be checked for (like fopen returning NULL)

Sometimes you see this..  :o 

/* make sure param isn't NULL */  <- ahhhhhhhh
int my_func(char *param)
{
  :
  :
}

.. I have on occasion caught myself doing that.. ;) 

Just my opinion of course, you may disagree. Indeed I work with people who go for the check-everything-at-every-possible-layer approach (and their code is so slow it has to be re-written half the time  ;-) ) .. But they get paid twice as much as me, so what do I know.... [-(

---

