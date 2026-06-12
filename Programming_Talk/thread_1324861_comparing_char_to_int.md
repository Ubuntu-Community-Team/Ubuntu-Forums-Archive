---
title: "comparing char to int"
date: 2009-11-12
forum: Programming Talk
---

### Post by BoilerEE on 2009-11-12
I am attempting to compare an int value to an int stored as a char, basically what I am doing is the code below

```

#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int main()
{
  char th,hund,ten,one,th_t,hund_t,ten_t,one_t;
  int year;
  char *yeer;

  yeer = malloc(sizeof(char)*4);
  th_t = '1';
  hund_t = '9';
  ten_t = '9';
  one_t = '0';
  year = 1990;
 
  th=(year/1000);
  hund=((year%1000)/100);
  ten=((year%100)/10);
  one=(year%10);
  if(th==th_t){
  printf("%d %d %d %d\n", th,hund,ten,one);
  printf("%d %d %d %d\n",th_t,hund_t,ten_t,one_t);
  }
  return(0);
}

```

I want to try to use the ascii values for both but do not know how to make the char ints into the ascii values. 

Thank you

---

### Post by froggyswamp on 2009-11-12
Maybe this
[http://www.ozzu.com/programming-forum/how-convert-char-into-int-t271.html](http://www.ozzu.com/programming-forum/how-convert-char-into-int-t271.html)

---

### Post by BoilerEE on 2009-11-12
ok that changed the output of the values that were declared as a char, but for the th, hund, ten, and one that I got from an int value still remain an int rather than their ascii values I changed the code to 

```


int main()
{
  char th,hund,ten,one,th_t,hund_t,ten_t,one_t;
  int year;
  char *yeer;

  yeer = malloc(sizeof(char)*4);
  th_t = '1';
  hund_t = '9';
  ten_t = '9';
  one_t = '0';
  year = 1990;

  th_t = (int)th_t;
  hund_t = (int)hund_t;
  ten_t = (int)ten_t;
  one_t = (int)one_t;

  th=(int)(year/1000);
  hund=(int)((year%1000)/100);
  ten=(int)((year%100)/10);
  one=(int)(year%10);
 
  printf("%d %d %d %d\n", th,hund,ten,one);
  printf("%d %d %d %d\n",th_t,hund_t,ten_t,one_t);

  return(0);
}

```
and the out put is
```

 a.out
1 9 9 0
49 57 57 48

```
it is the 1 9 9 0 that I want read as ascii any ideas... and I am sorry if I appear a little dumb...

---

### Post by lavinog on 2009-11-13
> **BoilerEE said:**
> o
```

 a.out
1 9 9 0
49 57 57 48

```
it is the 1 9 9 0 that I want read as ascii any ideas... and I am sorry if I appear a little dumb...

the 49 57 57 48 are the ascii values.
Are you wanting to output each digit as a char?
try:
```
  printf("%c %c %c %c\n",th_t,hund_t,ten_t,one_t);

```

---

### Post by lisati on 2009-11-13
"char" is designed for displaying stuff, and "int" is designed for computation. To compare one with the other, you'll need to do some kind of conversion.

The conversion usually includes something like subtracting the [ASCII]("http://en.wikipedia.org/wiki/ASCII") code for '0' (Zero) from the displayable value to get it into binary/int, or adding the ASCII code for '0' to the binary/int value to make it char.

---

### Post by samjh on 2009-11-13
> **BoilerEE said:**
> it is the 1 9 9 0 that I want read as ascii any ideas... and I am sorry if I appear a little dumb...

Just to clarify, are you wanting to print the ASCII values for each of 1, 9, 9, and 0, as though as are chars (not ints)?  In other words, convert the 1990 in year, to characters, then print the ASCII values for each character?

If so, you're going about it the wrong way.

First of all, there is no standard way to convert an int to a char.  Such functions exist in some C libraries as itoa(), but it is not part of ANSI/ISO C.  The closest thing you can get is using the sprintf() or snprintf() functions, which will allow you to "print" a number into a character buffer (ie. a string).  The problem with this is, you want the number turned into individual characters, not a string...

So, here is the way to do it:
[list=1][*]Declare a string (ie. char temp[4]).
[*]Convert the value in year to a string (ie. use the sprintf() or snprintf() functions).
[*]Assign each character in the temp[4] string to each of the variables th, hund, ten, and one (eg. th = temp[0] and so on).
[/list]

The difference between sprintf and snprintf is that the latter allows you to specify how many characters to print into the buffer.  In your case, it should be 5 characters, which includes the 4 digits and the termination character ('\0').  From a security perspective, snprintf is the safer of the two, since can help to prevent buffer overrun errors.

---

### Post by BoilerEE on 2009-11-13
actually I found a REALLY easy way to do it...
just add 48 to each int... it works because they are 48 away from the ASCii values. Might not work everywhere BUT works good enough for me.

---

### Post by benj1 on 2009-11-13
```

float strint (string s) 
{	
	stringstream ss (s);
	float a;
	ss >> a; 
	return a;
}

```

this is C++, don't know if it would work in C

---

### Post by LKjell on 2009-11-13
You can check out atoi for a string convert to int in a visible present.

---

