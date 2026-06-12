---
title: "Need help with my C program."
date: 2010-08-02
forum: Programming Talk
---

### Post by Cammaaron on 2010-08-02
When I try to run my program I will get a Segmentation fault error.

When I compile the code I get the warnings
```
math.c: In function ‘programone’:
math.c:63: warning: format ‘%f’ expects type ‘float *’, but argument 2 has type ‘double’
math.c:65: warning: format ‘%f’ expects type ‘float *’, but argument 2 has type ‘double’
math.c:67: warning: format ‘%f’ expects type ‘float *’, but argument 2 has type ‘double’

```

Here is the source code, I got line 63, 65, and 67 marked with** ">>> "**
```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int jsw_flush(void);
int programone(void);
int main()
{
    char c;
    for (;;)
    {
    printf("1: solve for right triangle \n");
    printf("0: Exit program\n");
    printf("\nSelect Your choice: ");
    c = getchar();
    jsw_flush();
    printf("\n");
    if(c=='0')
    {
    break;
    }
    switch (c)
        {
        case '1':
        programone();
        break;
        case '0':
        break;
        default:
        printf("wrong choice\n");
        break;

        }
    }
    return(0);
}    

int jsw_flush (void)
{
  int ch; /* getchar returns an int */

  /* Read characters until there are none left */
  do
    ch = getchar();
  while (ch != EOF && ch != '\n');

  clearerr (stdin); /* Clear EOF state */ 
  }
  
  programone(void)
  {
  
  float x = 0.0;
  float y = 0.0;
  float z = 0.0;
  float answer = 0.0;
  char c;
  for (;;)
  {
  printf("Please enter what numbers you know for the triangle\n"); 
  printf("If all numbers are entered, it will test to see if this is a right triangle\n");
  printf("\nWhat is the first side: ");
** >>>  **scanf("%f",x);
  printf("\nWhat is the second side: ");
**  >>>** scanf("%f",y);
  printf("\nWhat is the long side: ");
 ** >>> **scanf("%f",z);
  printf("\n");
  if (x = 0)
  {
  x = (sqrt(pow(z,2)-pow(y,2)));
  printf ("The answer is : %f.\n", x);
  }
  else if (y = 0)
  {
  y = (sqrt(pow(z,2)-pow(x,2)));
  printf ("The answer is : %f.\n", y);
  }
  else if (z=0)
  {
  z=(sqrt(pow(x,2)+pow(y,2)));
  printf("The answer is : %f\n",z);
  }
  else if (x!=0&&y!=0&&z!=0)
  {
  answer = (sqrt(pow(x,2) + pow(y,2)));
  if (answer=z)
  {
  printf ("This is a right triangle.\n");
  }
  else
  {
  printf ("This is not a right triangle.\n");
  }
  }
  
  printf("Do you want to another one? (y or n)\n");
  c = getchar();
    jsw_flush();
    if (c!='y'||c!='Y')
    {
    break;
    }
    
    
  }
  }
```

---

### Post by Queue29 on 2010-08-03
You need an ampersand in front of the x, y, and z.

[http://www.cplusplus.com/reference/clibrary/cstdio/scanf/](http://www.cplusplus.com/reference/clibrary/cstdio/scanf/)

ex:
```
scanf("%f", &x);
```

---

### Post by dwhitney67 on 2010-08-03
Here's your code again, but with the syntax errors corrected.

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

void jsw_flush(void); void programone(void); int main(void) { char c; for (;;) { printf("1: solve for right triangle \n"); printf("0: Exit program\n"); printf("\nSelect Your choice: "); c = getchar(); jsw_flush(); printf("\n"); if(c=='0') { break; } switch (c) { case '1': programone(); break; case '0': break; default: printf("wrong choice\n"); break; } } return(0); }    void jsw_flush (void) { int ch; /* getchar returns an int */ /* Read characters until there are none left */ do ch = getchar(); while (ch != EOF && ch != '\n'); } void programone(void) { float x = 0.0; float y = 0.0; float z = 0.0; float answer = 0.0; char c; for (;;) { printf("Please enter what numbers you know for the triangle\n"); printf("If all numbers are entered, it will test to see if this is a right triangle\n"); printf("\nWhat is the first side: "); scanf("%f",&x); printf("\nWhat is the second side: "); scanf("%f",&y); printf("\nWhat is the long side: "); scanf("%f",&z); printf("\n"); if (x == 0) { x = (sqrt(pow(z,2)-pow(y,2))); printf ("The answer is : %f.\n", x); } else if (y == 0) { y = (sqrt(pow(z,2)-pow(x,2))); printf ("The answer is : %f.\n", y); } else if (z==0) { z=(sqrt(pow(x,2)+pow(y,2))); printf("The answer is : %f\n",z); } else if (x!=0&&y!=0&&z!=0) { answer = (sqrt(pow(x,2) + pow(y,2))); if (answer==z) { printf ("This is a right triangle.\n"); } else { printf ("This is not a right triangle.\n"); } } printf("Do you want to another one? (y or n)\n"); c = getchar(); jsw_flush(); if (c!='y'||c!='Y') { break; } } }

```


P.S.  I found your code hard to read because of the crazy indenting; hopefully you will find my version equally challenging.

---

### Post by trent.josephsen on 2010-08-03
Don't use scanf for interactive input.  Use fgets and pick out the number with strtod, or write your own function using getchar() and friends.

Good explanations [here](http://c-faq.com/~scs/cclass/krnotes/sx10d.html) and [here](http://c-faq.com/stdio/scanfprobs.html).

---

### Post by smdawson on 2010-08-29
I had a quick question about scanf. I have a do-while loop that asks the user if they want to repeat at the end of a calculation by choosing (y/n). When I run the program it doesn't stop to allow the input of a character. The problem line:

```
scanf("%c", &repeat);
```

However, when I changed it to an integer the program stopped and waited for input from the user. The line of code was changed to this:

```
scanf("%i", &repeat);
```

What am I missing?

---

### Post by Bachstelze on 2010-08-29
You probably have a newline character waiting in the input buffer. Do not forget to flush it after each input. And also do not use scanf, see the links posted by trent.

---

