---
title: "Help with C error 'conflicting types'"
date: 2010-09-09
forum: Programming Talk
---

### Post by smdawson on 2010-09-09
I am trying to round money to the nearest cent. When I change calcStartBalance to return type int it works, but not with double. I keep getting the error 'conflicting types for function calcStartBalance'. help?

This is the problem piece of the code I have:

```
#define HUNDRED 100.00
#define POINT005 0.005

double roundToHundreths(double a)
{
  double b = 0.0;
  b = a + POINT005;
  b *= HUNDRED;
  b = (int)b;
  b /= HUNDRED;
  return b;
}

double calcStartBalance(double start_b, double down_p)
{
  return (roundToHundreths(start_b - down_p));
}
```

---

### Post by dwhitney67 on 2010-09-09
The code you posted works fine on my system; this is what I used:
```

#include <stdio.h>

#define HUNDRED 100.00
#define POINT005 0.005

double roundToHundreths(double a)
{
  double b = 0.0;
  b = a + POINT005;
  b *= HUNDRED;
  b = (int)b;
  b /= HUNDRED;
  return b;
}

double calcStartBalance(double start_b, double down_p)
{
  return (roundToHundreths(start_b - down_p));
}

int main()
{
   printf("%5.2lf\n", calcStartBalance(101, 5.43333));
   return 0;
}

```

P.S.  This works too:
```

double roundToHundreths(double a)
{
  return (int)((a + POINT005) * HUNDRED) / HUNDRED;
}

```

---

### Post by smdawson on 2010-09-09
I was able to get yours to compile, but mine still will not..Here is all the code I am trying to compile. I even broke it up smaller and tried to compile a segment the size of yours and that did not work either.

```
#include <stdio.h>
#define HUNDRED 100.00
#define POINT005 0.005


int main(void)
{
  double start_balance = 0.0;
  double down_payment = 0.0;
  double air = 0.0;
  double month_payment = 0.0;
  double new_balance = 0.0;

  printf("Enter the selling price: ");
  scanf("%lf", &start_balance);

  printf("Enter the down payment: ");
  scanf("%lf", &down_payment);

  printf("Enter the anual interest rate: ");
  scanf("%lf", &air);

  printf("Enter the monthly payment: ");
  scanf("%lf", &month_payment);

  new_balance = calcStartBalance(start_balance, down_payment);
  printf("The loan amount: %5.2lf\n", new_balance);

}

double roundToHundreths(double a)
{
  double b = 0.0;
  b = a + POINT005;
  b *= HUNDRED;
  b = (int)b;
  b /= HUNDRED;
  return b;
}

double calcStartBalance(double start_b, double down_p)
{
  return (roundToHundreths(start_b - down_p));
}

double canBePaid(double month_p, double interest)
{
  return (roundToHundreths(month_p - interest));
}

double calcInterest(double air, double new_b)
{
  return (roundToHundreths(air * new_b));
}

double calcNewBalance(double old_b, double to_b)
{
  return (roundToHundreths(old_b - to_b));
}

```

p.s. - any criticisms you have about good coding practices I am not following are welcome  :)

---

### Post by Some Penguin on 2010-09-09
It's probably 'problem unrelated', but your main() method declares an int return type without actually having a return statement.  It also probably wouldn't hurt to add a function prototype (pref. in a header file) to avoid the compiler producing any implicit declarations.

---

### Post by dwhitney67 on 2010-09-09
> **Some Penguin said:**
> ... It also probably wouldn't hurt to add a function prototype (pref. in a header file) to avoid the compiler producing any implicit declarations.
That's the ticket!  The OP presented one thing in his opening post, then something different later.

@ the OP:  When you compile your source code, use the -Wall option and correct any/all warnings.

---

### Post by smdawson on 2010-09-09
Sorry guys, I didn't know about prototyping the functions. After I did that it got rid of the errors.

 Also, should I use pointers for everything in my functions?
like this example I found [here]("http://www.java2s.com/Tutorial/C/0160__Function/Functionisdefinedaftermainprototypethefunction.htm")

```
#include <stdio.h>

f1(int *k);

main ( ){
    int i;

    i = 0;
    printf (" The value of i before call %d \n", i);
    f1 (&i);
    printf (" The value of i after call %d \n", i);
}

f1(int *k)
{
    *k = *k + 10;
}

```

---

### Post by worseisworser on 2010-09-09
Nope, F1 could just be passed values, then return its result as a value too, then the code after the call to F1 could assign, or not; thus using a functional style of programming as opposed to the imperative style seen in the example.

(..I'm typing this on my phone; someone can probably show you a code example..)

---

### Post by dwhitney67 on 2010-09-09
dawson,

always show full prototypes; don't leave off the 'int' simply because it is implied by the compiler.

Using a pointer for the example you provided is not esthetically pleasing.  The following would have been better:
```

#include <stdio.h>

**int **f1(**int k**);

**int** main (){
    **int i = 0;**    // always initialize your variables

    printf (" The value of i before call %d \n", i);
    **i = f1 (i);**
    printf (" The value of i after call %d \n", i);

    **return 0;**
}

**int** f1(**int k**)
{
    **return k * 10;**
}

```

---

### Post by smdawson on 2010-09-09
Ok. So always write full prototypes and I don't need to use pointers in the functions; I can just pass values. Thank you for all the help.

---

### Post by dwhitney67 on 2010-09-10
> **smdawson said:**
> Ok. So always write full prototypes and I don't need to use pointers in the functions; I can just pass values. Thank you for all the help.

Sometimes you will have to pass a pointer to a function; it just so happens that in the case you presented, it was not necessary.

In other cases, such as when calling the stat() C library function, it is necessary.  For example:
```

...

struct stat info;

int result = stat("/some/file", &info);

if (result == 0)
{
   // structure 'info' has relevant information about the
   // file /some/file.
}

```

---

### Post by smdawson on 2010-09-10
> **dwhitney67 said:**
> Sometimes you will have to pass a pointer to a function; it just so happens that in the case you presented, it was not necessary.

Ok, so I can just check the documentation of functions I use and that should let me know if parameters need to be a pointer or not? Or is there a rule-of-thumb about using or not using pointers?

---

### Post by dwhitney67 on 2010-09-10
> **smdawson said:**
> Ok, so I can just check the documentation of functions I use and that should let me know if parameters need to be a pointer or not? Or is there a rule-of-thumb about using or not using pointers?

As with most things in life, you will learn when to do something, and when not too.

Presenting your code online for a peer review was a good choice.  Software development companies often times require their developers to have in-house peer reviews.

Good luck with your learning.

---

