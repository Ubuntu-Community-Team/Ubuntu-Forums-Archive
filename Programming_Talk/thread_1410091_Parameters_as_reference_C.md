---
title: "Parameters as reference C"
date: 2010-02-18
forum: Programming Talk
---

### Post by cristiangarofalo on 2010-02-18
Hi, I'm starting with C and I have a problem that seems to be pretty easy but i'm not able to figured out what the problem is, I want to make a function that modifies a global variable, as easy as that, so passing a simple string by reference and modify the value of the global variable. 
this is not working compiler says: 
warning: passing argument 1 of ‘test’ from incompatible pointer type

can anyone help me? do you understand what im trying to do :s ? Thank you and regards to all !

void test(char *p)
{
printf("received->%s\n",*p);
char aux[]="BYE";
*p=aux;
}

int main(void)
{
char p[]="HELLO";
test(&p);
printf("modified by funct->%s\n",p);
return 0;
}

---

### Post by talonmies on 2010-02-18
What you are trying to do is invalid for several reasons:

[LIST=1]
[*]passing the address of p to test is incorrect
[*]p is a character array, not a pointer to char, so you can't set its value to a different pointer value pointer to char
[*]trying to use aux outside of the scope of test() is invalid
[/LIST]

---

### Post by CHW on 2010-02-18
Hi,

You have to cast p[] to (char*)p.
You have also a problem with char aux[], it's a local variable, it will be destroyed if you leave the function, sou you can't point at.

You could copy the content of aux into p. But this simple version only works if BYE < Hello, else you have to (re)allocate the memory you need.

Try this code:

```
void test(char *p)
{
  printf("received->%s\n",p);
  char aux[]="BYE";
  int i;
  for(i=0;i<3;i++) p[i] = aux[i];
  p[3]='\0'; // string end
}

int main(void)
{
  char p[]="HELLO";
  test((char*)p);
  printf("modified by funct->%s\n",p);
  return 0;
}
```

Note also that you have to write p instead of *p at printf.
To use *p this would be appropriate but prints only one character:
```
printf("received->%c\n",*p);
```

---

### Post by Bachstelze on 2010-02-18
Since you declared your strings using the bracket notation, you can't reassign them, so you have to use something like strcpy or memcpy to copy the new string onto the ld one:

```
#include <stdio.h>
#include <string.h>
#define STRINGMAXLENGTH 7

void test(char *p)
{
        printf("received->%s\n", p);
        char aux[]="BYE";
        strncpy(p, aux, STRINGMAXLENGTH);
}

int main(void)
{
        char p[STRINGMAXLENGTH+1] = "HELLO";
        test(p);
        printf("modified by funct->%s\n", p);
        return 0;
}

```

It is also a good idea to explicitly specify a maximum length to strings, in order to avoir buffer overflows.

---

### Post by cristiangarofalo on 2010-02-18
> **talonmies said:**
> What you are trying to do is invalid for several reasons:

[LIST=1]
[*]passing the address of p to test is incorrect
[*]p is a character array, not a pointer to char, so you can't set its value to a different pointer value pointer to char
[*]trying to use aux outside of the scope of test() is invalid
[/LIST]
Can you please help me with an example of how to do what i'm trying? 
What i'm trying to do is to copy the content of aux[] (in a subfunction) into the variable p[] on the main. that's why i understand i'm not using aux outside of the scope of test()

---

### Post by cristiangarofalo on 2010-02-18
> **Bachstelze said:**
> Since you declared your strings using the bracket notation, you can't reassign them, so you have to use something like strcpy or memcpy to copy the new string onto the ld one:

```
#include <stdio.h>
#include <string.h>
#define STRINGMAXLENGTH 7

void test(char *p)
{
        printf("received->%s\n", p);
        char aux[]="BYE";
        strncpy(p, aux, STRINGMAXLENGTH);
}

int main(void)
{
        char p[STRINGMAXLENGTH+1] = "HELLO";
        test(p);
        printf("modified by funct->%s\n", p);
        return 0;
}

```

It is also a good idea to explicitly specify a maximum length to strings, in order to avoir buffer overflows.
Cool!!! 
THANK YOU ALL ! I'm begginer and need to learn a lot! thanks again

---

### Post by napsy on 2010-02-18
There's no need to explicitly cast char[] to char* since the compiler does that implicitly.

---

